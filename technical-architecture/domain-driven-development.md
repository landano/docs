# Domain-driven development

Landano is a software-intensive system developed using [Domain Driven Design](https://en.wikipedia.org/wiki/Domain-driven\_design) (DDD) concepts and practices from the software engineering discipline. DDD focuses on the subject area to which the software is applied. For Landano that includes documenting, storing, verifying and exchanging land rights.\
\
The Mendix platform we are using to develop Landano enables model-driven development through Mendix Studio which provides visual drag-and-drop tools for workflows, user interfaces, data, logic, and navigation. Mendix interprets the resulting model at runtime thereby maintaining the bond between model and application which improves greatly upon managing legacy code and technical debt once a platform is in production.

<figure><img src="../.gitbook/assets/screenshot-2024-04-23-at-5.35.53 pm (1).png" alt=""><figcaption><p>The LADM in Mendix Studio</p></figcaption></figure>

### The Land Administration Domain Model (LADM)

Landano software and record-keeping requirements are compliant with specifications from the International Organization for Standardization (ISO) to ensure the sustainability, interoperability, credibility and legal value of the land right documentation that Landano creates and manages. \
\
The foundational model that drives the Landano domain is based on [ISO standard 19152](https://www.iso.org/standard/81263.html), the Land Administration Domain Model (LADM). The LADM provides a standardized global vocabulary and entity model for land administration. It has become the predominant reference standard for land administration software systems.\
\
Landano has implemented the LADM as a Mendix domain underpinning our business logic.

