[![Gitter](https://badges.gitter.im/aztfmod/community.svg)](https://gitter.im/aztfmod/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

# Deploys Service Health Alerts
This module tracks the following types of health events (subscription wide) and send alerts:

1. Service issues - Problems in the Azure services that affect you right now.

2. Planned maintenance - Upcoming maintenance that can affect the availability of your services in the future.

3. Health advisories - Changes in Azure services that require your attention.

4. Security advisories - Security related notifications or violations that may affect the availability of your Azure services.

Ref : https://docs.microsoft.com/en-us/azure/service-health/service-health-overview

An Action Group will be created and your choice of Notifications type can be chosen dynamically (refer input syntax).

## Requirements

No requirements.

## Providers

| Name | Version |
|------|---------|
| azurecaf | n/a |
| azurerm | n/a |

##  Input Syntax
```hcl
  # refer example configuration file
   monitoring = {
    service_health_alerts = {
        enable_service_health_alerts = true/false
        name = "<string>"
        action_group_name = "<string>"
        shortname = "<string>"
        resource_group_key = "<string>"

        email_alert_settings = {
          email_alert1 = {
            name = "<string>"
            email_address = "<emailAddress>"
            use_common_alert_schema = true/false
          }
          #remove the following block if additional email alerts aren't needed.
          email_alert2 = {
            name = "<string>"
            email_address = "<emailAddress>"
            use_common_alert_schema = true/false
          }
          ##add more email alerts by repeating the block.
        }

        #comment out this block exclude this configuration completely
        sms_alert_settings = {
          sms_alert1 = {
             name = "<string>"
             country_code ="<countryCode>"
             phone_number = "<phoneNumber>"
           } #follow the syntax of email alert settings to have one or more alerts
        }

        #comment out this block exclude this configuration completely
        #webhook = {
        #  webhook1 = {
          #   name = "<string>"
          #   service_uri = "<URI>"
          # } #follow the syntax of email alert settings to have one or more alerts
        #}

        #comment out this block exclude this configuration completely
        arm_role_alert = {
          arm_alert1 = {
            name = "<string>"
            use_common_alert_schema = true/false
            role_name = "Contributor" # Use the Built-in role names
          } #follow the syntax of email alert settings to have one or more alerts
        }

  }

}

}
```
