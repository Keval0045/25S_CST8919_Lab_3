# Azure Policy Lab – MapleTech Secure Foundation

## Summary

This lab demonstrates how Azure Policy can enforce governance and compliance in a cloud environment. Acting as a new Cloud Security Engineer at MapleTech Solutions, I used Azure Policy and initiatives to enforce three key organizational rules:

- Resources must only be deployed in **Canada Central**
- Every resource must have a **ProjectName tag**
- No **Public IP addresses** are allowed

## Policies Created

### 1. **Only-CanadaCentral**
- **Effect**: Deny
- **Description**: Blocks resource deployment in any region other than Canada Central.

### 2. **Require-ProjectName-Tag**
- **Effect**: Deny
- **Description**: Requires all resources to include a `ProjectName` tag before deployment.

### 3. **Deny-Public-IP**
- **Effect**: Deny
- **Description**: Prevents creation of Public IP resources in the environment.

## Initiative

### MapleTech Secure Foundation
- Combines the three policies above.
- Assigned at the subscription level.
- Enforces security and compliance automatically.

## Testing Results

| Test Case                                      | Result     |
|-----------------------------------------------|------------|
| Deploy VM in East US                          | ❌ Denied  |
| Deploy storage without ProjectName tag        | ❌ Denied  |
| Create a Public IP                            | ❌ Denied  |
| Deploy VM in Canada Central with valid tag    | ✅ Allowed |

## Screenshots

All enforcement test case screenshots are in the `screenshots/` folder.

## Lessons Learned

- Azure Policy is powerful and straightforward once definitions are clear.
- Always test individual policies before bundling into an initiative.
- Enforcing policies at the **initiative** level ensures consistent governance.
