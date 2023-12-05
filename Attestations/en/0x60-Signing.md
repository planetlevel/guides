# Signing
CycloneDX supports signing to ensure the authenticity and integrity of the attestations. This is crucial for 

* `Verification of Origin`: Signed SBOMs and attestations provide verifiable evidence of their origin, preventing unauthorized tampering or impersonation.

* `Non-Repudiation`: Signing prevents the signer from denying the authenticity of the signed content, ensuring accountability and traceability.

* `Integrity Assurance`: Signing guarantees that the signed content has not been modified or altered after it was signed, safeguarding the integrity of the information.

## Signatories
The personas that could sign claims, evidence, standards, or attestations can be categorized into two main groups:

* `Producers`: These are the entities responsible for creating and managing the SBOMs and attestations. They could include:
    * `Software developers`: Developers of software components or applications are often responsible for generating claims that accurately reflect their Software Development Lifecycle (SDL).
    * `Software distributors`: Distributors of software packages may create SBOMs that aggregate the SBOMs of individual components included in their packages and provide assurances for the software packages in the form of assurances.
    * `Build or deployment tools`: Automated build or deployment tools can generate SBOMs and evidence for supporting the claims required by the developers as part of their workflow, ensuring that the SBOMs are up-to-date with the latest code changes and the claims are supported .
    * `Software supply chain security tools`: Security tools can analyze SBOMs to identify potential vulnerabilities, compliance issues, or other relevant information and generate evidence of security testing and validation.
* `Verifiers`: These are the entities responsible for validating and verifying the authenticity and integrity of SBOMs or attestations. They could include:
    * `Organizations consuming software`: Organizations that use or integrate software components may require attestations that meet a certain standard. (e.g: PCI-DSS certified software)
    * `Regulatory bodies or auditors`: Regulatory bodies or auditors may use the claims, evidence and attestation generated by the software producers as part of compliance audits or certification processes.

In some cases, a single entity may act as both a producer and a verifier of SBOMs or attestations. For example, a software development company may generate SBOMs and attestations for its own products and also verify them from its suppliers.

The specific personas involved in signing CycloneDX claims, evidence, standards, or attestations will depend on the specific context and the intended use of the attestations. However, the producer and verifier roles are typically involved in establishing trust and ensuring the integrity of the information being conveyed.

### Digital Signatures
CycloneDX supports multiple digital signing methods to accommodate various preferences and security requirements. These methods include:

* `XML Signature (xmlsig)`: This is a widely used XML-based signing format that provides a standard way to sign XML documents.
* `JSON Signature Format (JSF)`: This is a lightweight JSON-based signing format that offers a more compact and efficient alternative to XML Signature for signing CycloneDX attestations.
* `Detached Signatures`: Detached signatures allow the signature to be stored separately from the signed content, providing flexibility and reducing the size of the signed document.

### Analog Signatures
CycloneDX supports use of analog signatures for signing CycloneDX attestations. Analog signatures are typically used for signing paper documents and are not as secure as digital signatures. However, they can be useful in some cases where digital signatures are not available or practical. CycloneDX does not mandate the use of analog signatures, and the specific format of an analog signature will vary depending on the context and the signing mechanism used. However, CycloneDX recommends the use of the following format for analog signatures:

* `Signature Image`: A scanned image of the signature.
* `Signature Text`: The text of the signature.
* `Signature Date`: The date when the signature was created.
* `Signature Location`: The location where the signature was created.
* `Signature Type`: The type of signature (e.g: handwritten, electronic, etc.)

Here are some specific examples of when analog signatures might be used in CycloneDX attestations:

* `Verifying the identity of a software supplier`: When a software supplier is required to provide an attestation to a customer, the supplier may use an analog signature to verify their identity and the authenticity of the attestation.
* `Attesting to the compliance of software with regulations`: An analog signature may be used to attest to the software's compliance.

In general, analog signatures are a useful way to add an extra layer of assurance to CycloneDX attestations, especially when dealing with physical documents or legacy systems. 

## Signing for Authenticity
CycloneDX supports signing to ensure the authenticity and integrity of the attestations. This is crucial for detecting unauthorized tampering or impersonation. Digital signing methods are used to ensure the authenticity of the attestations. 

## Digital Signatures
CycloneDX supports multiple digital signing methods to accommodate various preferences and security requirements - xmlsig, JSF, and detached signatures. 

Example of a CycloneDX attestation with a digital signature:

```xml
<attestation>
  <signature algorithm="RS512">
    <publicKey>
      <kty>RSA</kty>
      <n>qOSWbDOGS31lv3aUZVOgqZyLVrKXXRfmxFQxEylc...</n>
      <e>AQAB</e>
    </publicKey>
    <value>HGIX_ccdIcqmaOpkxDzKH_j0ozSHUAUyBxGpXS...</value>
  </signature>
</attestation>
```

```json
"signature": {
  "algorithm": "RS512",
  "publicKey": {
    "kty": "RSA",
    "n": "qOSWbDOGS31lv3aUZVOgqZyLVrKXXRfmxFQxEylc...",
    "e": "AQAB"
  },
  "value": "HGIX_ccdIcqmaOpkxDzKH_j0ozSHUAUyBxGpXS..."
}
```

<!-- TODO: Detached Signature example -->