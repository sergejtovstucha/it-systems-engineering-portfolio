# Production Asterisk Migration — VMware to Hyper-V

**Project type:** Production infrastructure migration / systems integration  
**Technologies:** VMware, Hyper-V, Linux, Asterisk PBX, MySQL/MariaDB, Apache, PHP web application, SIP

## Business objective

Move an existing production Asterisk PBX and its supporting web application from VMware to Hyper-V while keeping telephony service interruption as short and predictable as possible.

## My responsibilities

I performed the server preparation, application and database migration, validation, and final cutover. The target was rebuilt rather than treated as a simple virtual disk conversion.

## Migration workflow

1. **Prepare the target environment.** Create the Hyper-V virtual machine and install the operating system and required services: Asterisk, MySQL/MariaDB and Apache.
2. **Restore the PBX configuration.** Copy the relevant Asterisk configuration from the original server to the new installation.
3. **Migrate application data.** Export and restore the database; deploy the web application and restore its Apache configuration.
4. **Validate before cutover.** Use a temporary SIP trunk to test PBX behaviour and connectivity without immediately replacing the production endpoint.
5. **Perform the cutover.** Switch the IP address / hostname to move the production service to the replacement system.
6. **Check service operation.** Verify the running PBX, associated services and expected call handling after the change.

## High-level migration sequence

```text
Original production VM (VMware)
  Asterisk + database + Apache/web app
                |
                | configuration, DB dump and application transfer
                v
New VM (Hyper-V)
  Rebuilt services + restored configuration and data
                |
                | temporary SIP trunk tests
                v
Validated target
                |
                | planned IP/hostname cutover
                v
Production service on Hyper-V
```

## Result

**Approximately 20 minutes of production downtime during the final cutover.** The majority of installation, transfer and testing work was completed before that cutover.

## Engineering considerations

- A PBX migration involves more than the Asterisk service: the database, administration interface, web-server configuration and SIP connectivity must all be accounted for.
- A temporary test trunk made it possible to validate important call scenarios before changing production routing.
- The exact sequence depends on the operating environment and the carrier's SIP trunk configuration; this is a case study, **not** a universal migration runbook.
- There are no published customer addresses, credentials, databases or internal configurations in this repository.

## Why it matters

This project demonstrates hands-on Linux administration, cross-hypervisor migration, telephony troubleshooting, database/application restoration and controlled service cutover in a production environment.

## Scope note

This description records the completed historical project. It does not claim zero downtime, automated failover, or a formally measured high-availability service level.
