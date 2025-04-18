# Approval Form Project

## Overview

The Approval Form Project is a Salesforce Lightning Web Component (LWC) application designed to streamline the approval process workflow. It provides a modern, user-friendly interface for users to select approval types, view configurations, and make approval decisions.

## Features

- **Modern UI Design**: Card-based layout with responsive design for different screen sizes
- **Intuitive Workflow**: Step-by-step visual flow with numbered sections
- **Dynamic Configuration**: Displays approval configurations based on selected approval type
- **Decision Making**: Clear accept/deny options with visual feedback
- **Real-time Updates**: Immediate feedback on submission status
- **Salesforce Integration**: Fully integrated with Salesforce data model

## Prerequisites

- Salesforce Developer or Enterprise Edition org
- Salesforce CLI installed
- Visual Studio Code with Salesforce Extensions
- Node.js and npm (for development)

## Installation

1. Clone this repository to your local machine
2. Authorize your Salesforce org:
   ```
   & "C:\Program Files\sf\bin\sf.cmd" org login web --set-default-dev-hub
   ```
3. Display org information for your target org:
   ```
   & "C:\Program Files\sf\bin\sf.cmd" org display --target-org mytargetorg
   ```
4. Deploy the project to your org:
   ```
   & "C:\Program Files\sf\bin\sf.cmd" project deploy start --manifest manifest/package.xml
   ```

## Configuration

### Custom Object Setup

This project relies on the `Approval_Config_Record__c` custom object with the following fields:

- `Approval_Type__c` (Text): Categorizes the approval record
- `Config_Name__c` (Text): Name of the configuration
- `Decision__c` (Text): Stores the approval decision (Accept/Deny)
- `Is_Approved__c` (Checkbox): Indicates if the record is approved

You'll need to create this custom object and its fields in your Salesforce org before using the component.

## Usage

1. After deployment, add the `approvalForm` component to any Lightning page using the Lightning App Builder
2. The component can be added to:
   - Record pages
   - App pages
   - Home pages
3. Using the component:
   - Select an approval type from the dropdown
   - Choose a specific configuration
   - Make your decision (Accept/Deny)
   - Submit your decision

## Component Structure

### Lightning Web Component
- **approvalForm**: Main LWC component with HTML, JS, and CSS files

### Apex Controller
- **ApprovalFormController**: Handles data operations and business logic
  - `getApprovalConfigs()`: Retrieves all approval configurations
  - `getDistinctApprovalTypes()`: Gets unique approval types for the dropdown
  - `getRecordsByApprovalType()`: Filters records by selected approval type
  - `updateDecision()`: Updates the decision field on a record

## Deployment

### Validate Deployment
```
& "C:\Program Files\sf\bin\sf.cmd" project deploy validate --manifest manifest/package.xml --target-org mytargetorg
```

### Deploy to Org
```
& "C:\Program Files\sf\bin\sf.cmd" project deploy start --manifest manifest/package.xml --target-org mytargetorg
```

### Check Deployment Status
```
& "C:\Program Files\sf\bin\sf.cmd" project deploy report --target-org mytargetorg
```

## Testing

Run Apex tests to verify functionality:
```
& "C:\Program Files\sf\bin\sf.cmd" apex run test --class-names ApprovalFormController --result-format human --target-org mytargetorg
```