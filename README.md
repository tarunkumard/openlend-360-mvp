# OpenLend 360 — Minimal MVP

A small, free starter for exploring commercial lending on the Salesforce platform. It gives you the core data model and one piece of automation, so you can deploy it to a Developer Edition org in a few minutes and see how a loan application, its documents, collateral and conditions fit together.

This is the **minimal** version. It is not the full OpenLend 360 build described in the [Force Apex Hours article](https://forceapexhours.com/build-a-commercial-lending-mvp-on-salesforce-fsc-inspired-workflows-self-service-and-ncino-style-lending-patterns/). The guided workspace, credit memo generator, stage-gate automation, approval routing, lifecycle Path and reports are not included. Treat it as a learning base, not a working lending system.

## What's in here

- **Data model:** Loan Application (with a Commercial Loan record type), Loan Product, Collateral, Guarantor, Loan Document Checklist Item, Loan Condition, Approval Request, Credit Memo and Loan Work Item, all built on standard Salesforce custom objects
- **Formula and roll-up fields** for collateral lendable value, total collateral, loan-to-value and document completion
- **Financial fields** for net operating income, annual debt service and DSCR (in this minimal version you enter DSCR yourself; the full build calculates it with a flow)
- **Validation rules** that keep the basic data clean
- **One record-triggered flow** that creates the required-document checklist when a loan application is created
- **Permission sets** for relationship manager, underwriter, credit approver, loan officer, operations and an administrator, plus two permission set groups
- Page layouts, tabs, list views, custom report types and the OpenLend 360 Lightning app

No managed packages and no Apex.

## Deploy it

You need the [Salesforce CLI](https://developer.salesforce.com/tools/salesforcecli) and a Developer Edition org or sandbox.

```bash
git clone https://github.com/tarunkumard/openlend-360-mvp.git
cd openlend-360-mvp

sf org login web --alias openlend-mvp
sf project deploy start --source-dir force-app/main --target-org openlend-mvp
sf org assign permset --name OpenLend_Administrator --target-org openlend-mvp
```

Then open the **OpenLend 360** app, create a Loan Product, and create a Loan Application with the Commercial Loan record type. The document checklist appears in the related list as soon as you save.

## Want the full build, or one tailored to your bank?

I help teams design and build commercial-lending solutions on Salesforce and Financial Services Cloud: architecture, data model, Flow automation, integrations and deployment. You can read more and get in touch through [forceapexhours.com](https://forceapexhours.com), or book a paid consultation at [paypal.me/tkdhealthtips](https://paypal.me/tkdhealthtips).

## Disclaimer

OpenLend 360 is an independent educational demonstration with fictional data. It is not a compliant loan origination system. Salesforce, Financial Services Cloud and nCino are trademarks of their respective owners. This project is not affiliated with or endorsed by nCino or Salesforce.

## License

MIT. See [LICENSE](LICENSE).
