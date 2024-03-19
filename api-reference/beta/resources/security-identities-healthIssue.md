---
title: "health issue resource type"
description: "Represents potential issues within a customer's Microsoft Defender for Identity configuration that Microsoft Defender for Identity have identified."
ms.date: 19/03/2024
author: "NaamaAlmog"
ms.localizationpriority: medium
ms.prod: "security"
doc_type: resourcePageType
---

# alert resource type

Namespace: microsoft.graph.security.identities

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

This resource corresponds to the latest generation of health issues in the Microsoft Graph security API, Represents potential issues within a customer's Microsoft Defender for Identity configuration that Microsoft Defender for Identity have identified.

## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List healthIssues](../api/security-identities-healthIssue-list-healthIssues.md)|[microsoft.graph.security.identities.healthIssue](security-identities-healthIssue.md) collection|Get a list of [healthIssue](../resources/security-identities-healthIssue.md) resources that have been created to track Microsoft Defender for Identity mis-configuration in an organization.|
|[Get healthIssue](../api/security-identities-healthIssue-get.md)|[microsoft.graph.security.identities.healthIssue](security-identities-healthIssue.md)|Get the properties of an [healthIssue](../resources/security-identities-healthIssue.md) object in an organization based on the specified healthIssue **id** property.|
|[Update healthIssue](../api/security-identities-healthIssue-update.md)|[microsoft.graph.security.identities.healthIssue](../resources/security-identities-healthIssue.md)|Update the properties of an [healthIssue](../resources/security-identities-healthIssue.md) object in an organization based on the specified healthIssue **id** property.|

## Properties
|Property|Type|Description|
|:---|:---|:---|

| Property       | Type           | Description                                 | Key       | Required  | ReadOnly  |
| -------------- | -------------- | ------------------------------------------- | --------- | --------- | --------- |
| id | Edm.String | Unique identifier to represent the health issue | Yes | Yes | Yes |
| displayName | Edm.String | The display name of the health issue | No | Yes | Yes |
| issueTypeId | Edm.String | The type identifier of the health issue. You can find a comprehensive list of all health issues and their identifiers at the following link: https://go.microsoft.com/fwlink/?linkid=2245397. | No | Yes | Yes |
| healthIssueType | microsoft.graph.security.HealthIssueType | The type of the health issue. You can find a comprehensive list of all health issues at the following link: https://go.microsoft.com/fwlink/?linkid=2245397. | No | Yes | Yes |
| severity | microsoft.graph.HealthIssueSeverity | The severity of the health issue. Possible values are Low, Medium and High. | No | Yes | Yes |
| status | microsoft.graph.HealthIssueStatus | The status of the health issue. Possible values are Open, Closed, and Suppressed. | No | Yes | No |
| createdDateTime | Edm.DateTimeOffset | The date and time of when the health issue was generated | No | Yes | Yes |
| lastModifiedDateTime | Edm.DateTimeOffset | The date and time of when the health issue was last updated | No | Yes | Yes |
| domainNames | Collection(Edm.String) | List of the fully qualified domain name of the domains or the sensors the health issue is realated to | No | Yes | Yes |
| sensorDNSNames | Collection(Edm.String) | List of the dns names of the sensors the health issue is realated to | No | Yes | Yes |
| description | Edm.String | More detailed information on the health issue | No | Yes | Yes |
| recommendations | Collection(Edm.String) | This field contains a list of recommended actions that can be taken to resolve the issue. These actions may include instructions on how to investigate the issue further, and they are not limited to pre-written responses. The recommended actions are intended to provide guidance on how to address the issue effectively and efficiently. | No | Yes | Yes |
| recommendedActionCommands | Collection(Edm.String) | This field may contain a list of commands from the product's PowerShell Module that can be used to resolve the issue, if available. If there are no commands that can be used to solve the issue, the field will be left empty. The commands, if present, are intended to provide a quick and efficient way to address the issue. These commands will be executed in order for the single recommended fix | No | Yes | Yes |
| additionalInformation | Collection(Edm.String) | Additional information on the issue, such as a list of items to fix | No | Yes | Yes |

#### HealthIssueSeverity values

| Member                     | Description                                                                                                                  |
| :--------------------------| :--------------------------------------------------------------------------------------------------------------------------- |
| low | Low severity health issues usually indicate minor issues that don't have a significant impact on your environment. These issues require further investigation, but they usually don't require immediate action. |
| medium | Medium severity health issues indicate more significant issues that could potentially impact your environment. These issues may require further investigation and action to prevent any potential problems. |
| high | High severity health issues indicate critical issues that could have a severe impact on your environment. These issues require immediate attention and action. |

#### HealthIssueStatus values

| Member                     | Description                                                                                                                  |
| :--------------------------| :--------------------------------------------------------------------------------------------------------------------------- |
| open | The issue is opened and should be addressed. |
| closed | The issue was addressed, either by someone manually closing the issue, by taking an action on the impacted item or automatically by the system. |
| suppressed | The issue was suppressed maually by an operator to be ignored for a period of time, depending on the type of the health issue. |

#### HealthIssueType values

| Member                     | Description                                                                                                                  |
| :--------------------------| :--------------------------------------------------------------------------------------------------------------------------- |
| Sensor | The issue is on specific sensor. |
| Global | The issue is in the defender for identity system configuration. |

## Relationships
None.

## JSON representation
The following is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.security.identities.healthIssue",
  "baseType": "microsoft.graph.entity",
  "openType": false
}
-->

``` json
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#security/identities/healthIssues",
    "value": [
        {
            "id": "b3c1b5fc-828c-45fa-a1e1-10d74f6d6e9c",
            "displayName": "Directory Services Object Auditing is not configured as required",
            "healthIssueType": "Global",
            "issueTypeId": "1031",
            "severity": "medium",
            "status": "open",
            "createdDateTime": "2022-07-15T12:19:27.7211305Z",
            "lastModifiedDateTime": "2022-07-15T12:19:27.7211305Z",
            "domainNames": ["domain1.contoso.com", "domain2.contoso.com"],
            "sensorDNSNames": [
                "DC1.domain1.contoso.com",
                "DC2.domain2.contoso.com"
            ]
            "description": "Directory Services Object Auditing is not configured as required on domain1.contoso.com",
            "recommendations": [
                "Please configure the Directory Services Object Auditing events according to the guidance as described in https://aka.ms/mdi/objectauditing"
            ],
            "recommendedActionCommands": [
                "Import-Module DefenderForIdentity",
                "Set-MDIConfiguration -Configuration DomainObjectAuditing -Mode Domain -Force"
            ],
            "additionalInformation": [
                "Descendant User Objects (Schema-Id-Guid: bf967aba-0de6-11d0-a285-00aa003049e2)",
                "Descendant Group Objects (Schema-Id-Guid: bf967a9c-0de6-11d0-a285-00aa003049e2)",
                "Descendant Computer Objects (Schema-Id-Guid: bf967a86-0de6-11d0-a285-00aa003049e2)",
                "Descendant msDS-GroupManagedServiceAccount Objects (Schema-Id-Guid: 7b8b558a-93a5-4af7-adca-c017e67f1057)",
                "Descendant msDS-ManagedServiceAccount Objects (Schema-Id-Guid: ce206244-5827-4a86-ba1c-1c0c386c1b64)"
            ]
        }
    ]
}
```

<!--
{
  "type": "#page.annotation",
  "namespace": "microsoft.graph.security"
}
-->