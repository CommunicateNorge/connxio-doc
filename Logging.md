# Logging

- [Logging](#logging)
  - [What does CX log?](#what-does-cx-log)
    - [Log-levels](#log-levels)
      - [None](#none)
      - [Minimum](#minimum)
      - [Standard](#standard)
      - [Verbose](#verbose)
  - [How to start logging](#how-to-start-logging)
    - [Archeo](#archeo)
    - [Webhook](#webhook)
  - [To log or not to log?](#to-log-or-not-to-log)

ConnXio (CX) lets customers use a variety of different logging options, solutions and setups. Communicate Norge offers our transaction-based logging software [Archeo](https://www.archeo.no/) as a supplement to ConnXio, and since we develop both products, the compatibility and feature richness is enhanced with this combination. However, we also support sending logs via webhook, which allows for logging to the customers logging provider of choice. This page details how to set up logging and how logging is configured.

We also offer total *integration as a service* where we handle logging, support, surveillance and fault detection on behalf of our customers. Please contact our sales department at <support@communicate.no> for further information.

## What does CX log?

CX sends logs from the internal engine to the configured logging provider every time a message is processed through a CX integration defined by the CX integration configuration. What logs are sent by CX is configured for each integration in accordance with customer needs. These options are detailed [below](#how-to-start-logging).

### Log-levels

CX operates with the term *log-levels*. A log-level is a set of logs that together define a level of information about the integrations journey through CX. Each log-level **includes the log from the less verbose layer**. The log-levels are as follows:

1. None - Nothing is logged except critical errors.
2. Minimum - The first inbound step and the last outbound step are logged.
3. Standard - All transformations are logged.
4. Verbose - All possible information is logged

#### None

The *None* log-level does not send any logs to the logging provider with a notable exception; if a logging provider is defined on the configuration and the *None* log-level is selected all critical errors are still logged. Since you could turn logging off just by not configuring a logging provider the *None* level lets you log only critical errors and nothing else. We would highly recommend always configuring a logging provider and setting this log level even if you don't want any regular logging for the integration, so that you can catch irregularities and patch them as needed.

#### Minimum

The *Minimum* log-level logs when the message is first seen by CX, this could be when the message is received by the API or picked from the chosen protocol like SFTP or Azure Storage. It also enables logs for the last time CX sees the message, this could be when the message is safely delivered to an SFTP folder or Service Bus topic. If you use the [Acknowledgement functionality](Adapters/Outbound/Acknowledgment.md), the acknowledgement message is also logged on this level.

#### Standard

This level includes the less verbose levels but also adds all transformation steps. This includes but is not limited to data collection, code mapping, integration account mapping, file encoding, format conversion. This level is recommended for non-trivial integrations that don't generate a lot of traffic. Traffic concerns are addressed [here](#to-log-or-not-to-log).

#### Verbose

The *Verbose* level logs every conceivable event of interest thorough CX. It could be seen as a debug level, and logs all transmission between internal CX engines, warning on retry or failed transient processes, initiation of external communication and more. This level is only recommended for debug purposes or for mission critical integrations.

## How to start logging

All logging providers are treated equally in relation to CX, and we do have a goal of adding provider specific convenience configuration for the largest providers in the future, currently however we only have a convenience configuration section for Archeo, but you can configure both Archeo and all other REST based providers by selecting the Webhook configuration option. To summarize we have two logging configuration options:

### Archeo

USe this convenience option if you want to send logs generated by CX to Archeo. This requires an [active Archeo subscription](https://www.archeo.no/pricing) that supports the amount of logs sent from CX.

### Webhook

## To log or not to log?