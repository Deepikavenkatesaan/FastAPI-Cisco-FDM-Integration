# FastAPI-Cisco-FDM-Integration

## Introduction

This FastAPI application provides a set of endpoints to interact with the Cisco Firepower Device Manager (FDM) API. It allows you to manage network objects, access policies, port objects, and NAT rules and other network objects.

## Example Usage
To get started, make sure you have the required dependencies installed. You can do this by running:

--->pip install fastapi requests uvicorn

Next, you can start the FastAPI server:

-->uvicorn main:app --reload

## Endpoints

### 1. Network Objects

GET /network_objects

Description: Get a list of network objects.

POST /create_network_object

Description: Create a new network object.

Request Body: JSON containing network object data.

DELETE /delete_network_object/{object_id}

Description: Delete a network object by its ID.

PUT /update_network_object/{object_id}

Description: Update a network object by its ID.

Request Body: JSON containing updated network object data.

### 2. Access Policy

GET /access_policies

Description: Get a list of access policies.

GET /get_access_rules/{policy_id}

Description: Get access rules for a specific policy by its ID.

POST /create_access_rule/{policy_id}

Description: Create a new access rule for a specific policy.

Request Body: JSON containing access rule data.

DELETE /delete_access_rule/{policy_id}/{rule_id}

Description: Delete an access rule by its ID.

PUT /update_access_rule/{parent_id}/{object_id}

Description: Update an access rule by its ID.

Request Body: JSON containing updated access rule data.

### 3. Port Objects

GET /get_port_objects/{limit}

Description: Get a list of port objects. You can specify a limit.

POST /create_port_object

Description: Create a new port object.

Request Body: JSON containing port object data.

DELETE /delete_port_object/{port_id}

Description: Delete a port object by its ID.

PUT /update_port_object/{object_id}

Description: Update a port object by its ID.

Request Body: JSON containing updated port object data.

### 4. NAT Rules

### Auto NAT Rules

GET /nat_auto_rules

Description: Get a list of auto NAT rules.

POST /create_nat_auto_rule

Description: Create a new auto NAT rule.

Request Body: JSON containing auto NAT rule data.

DELETE /delete_nat_auto_rule/{rule_id}

Description: Delete an auto NAT rule by its ID.

PUT /update_nat_auto_rule/{rule_id}

Description: Update an auto NAT rule by its ID.

Request Body: JSON containing updated auto NAT rule data.

### Manual NAT Rules

GET /nat_manual_rules

Description: Get a list of manual NAT rules.

POST /create_nat_manual_rule

Description: Create a new manual NAT rule.

Request Body: JSON containing manual NAT rule data.

DELETE /delete_nat_manual_rule/{rule_id}

Description: Delete a manual NAT rule by its ID.

PUT /update_nat_manual_rule/{rule_id}

Description: Update a manual NAT rule by its ID.

Request Body: JSON containing updated manual NAT rule data.

### Function Signature for retrieving authentication token

get_token(token: str = Depends(get_Token)) -> str

### Description: Retrieves the authentication token from the FDM API.


### Function Signature for retrieving a list of network objects
get_network(token: str = Depends(get_token)) -> dict
### Description: Retrieves a list of network objects.

### Function Signature for creating a network object
create_network_object(network_data: dict, token: str = Depends(get_token)) -> dict
### Description: Creates a new network object.
### Arguments:
### - network_data (dict): JSON containing network object data.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for deleting a network object
delete_network_object(object_id: str, token: str = Depends(get_token)) -> dict
### Description: Deletes a network object by its ID.
### Arguments:
### - object_id (str): ID of the network object to be deleted.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for updating a network object
update_network_object(object_id: str, network_object_data: dict, token: str = Depends(get_token)) -> dict
### Description: Updates a network object by its ID.
### Arguments:
### - object_id (str): ID of the network object to be updated.
### - network_object_data (dict): JSON containing updated network object data.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for retrieving a list of access policies
get_access_policies(token: str = Depends(get_token)) -> str
### Description: Retrieves a list of access policies.

### Function Signature for retrieving access rules for a specific policy
get_access_rules(policy_id: str, token: str = Depends(get_token)) -> dict
### Description: Retrieves access rules for a specific policy by its ID.
### Arguments:
### - policy_id (str): ID of the access policy.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for creating an access rule
create_access_rule(policy_id: str, access_rule_data: dict, token: str = Depends(get_token)) -> dict
### Description: Creates a new access rule for a specific policy.
### Arguments:
### - policy_id (str): ID of the access policy.
### - access_rule_data (dict): JSON containing access rule data.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for deleting an access rule
delete_access_rule(policy_id: str, object_id: str, token: str = Depends(get_token)) -> dict
### Description: Deletes an access rule by its ID.
### Arguments:
### - policy_id (str): ID of the access policy.
### - object_id (str): ID of the access rule to be deleted.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for updating an access rule
update_access_rule(parent_id: str, object_id: str, access_rule_data: dict, token: str = Depends(get_token)) -> dict
### Description: Updates an access rule by its ID.
### Arguments:
### - parent_id (str): ID of the access policy.
### - object_id (str): ID of the access rule to be updated.
### - access_rule_data (dict): JSON containing updated access rule data.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for retrieving a list of port objects
get_port_objects(limit: int, token: str = Depends(get_token)) -> dict
### Description: Retrieves a list of port objects. You can specify a limit.
### Arguments:
### - limit (int): Maximum number of port objects to retrieve.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for creating a port object
create_port_object(port_data: dict, token: str = Depends(get_token)) -> dict
### Description: Creates a new port object.
### Arguments:
### - port_data (dict): JSON containing port object data.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for deleting a port object
delete_port_object(port_id: str, token: str = Depends(get_token)) -> dict
### Description: Deletes a port object by its ID.
### Arguments:
### - port_id (str): ID of the port object to be deleted.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for updating a port object
update_port_object(port_id: str,  port_object_data: dict, token: str = Depends(get_token)) -> dict
### Description: Updates a port object by its ID.
### Arguments:
### - port_id (str): ID of the port object to be updated.
### - port_object_data (dict): JSON containing updated port object data.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for retrieving the ID of auto NAT rules
get_nat_objectid(token: str = Depends(get_token)) -> str
### Description: Retrieves the ID of auto NAT rules.

### Function Signature for retrieving auto NAT rules
get_nat_rules(parent_id: str, token: str = Depends(get_token)) -> dict
### Description: Retrieves auto NAT rules for a specific policy by its ID.
### Arguments:
### - parent_id (str): ID of the auto NAT policy.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for creating an auto NAT rule
create_nat_rule(parent_id: str, nat_rule_data: dict, token: str = Depends(get_token)) -> dict
### Description: Creates a new auto NAT rule.
### Arguments:
### - parent_id (str): ID of the auto NAT policy.
### - nat_rule_data (dict): JSON containing auto NAT rule data.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for deleting an auto NAT rule
delete_nat_rule(parent_id: str, object_id: str, token: str = Depends(get_token)) -> dict
### Description: Deletes an auto NAT rule by its ID.
### Arguments:
###- parent_id (str): ID of the auto NAT policy.
### - object_id (str): ID of the auto NAT rule to be deleted.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for updating an auto NAT rule
update_nat_rule(parent_id: str, object_id: str, nat_rule_data: dict, token: str = Depends(get_token)) -> dict
### Description: Updates an auto NAT rule by its ID.
### Arguments:
### - parent_id (str): ID of the auto NAT policy.
###- object_id (str): ID of the auto NAT rule to be updated.
### - nat_rule_data (dict): JSON containing updated auto NAT rule data.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for retrieving the ID of manual NAT rules
get_nat_objectid(token: str = Depends(get_token)) -> str
### Description: Retrieves the ID of manual NAT rules.

### Function Signature for retrieving manual NAT rules
get_nat_rules(parent_id: str, token: str = Depends(get_token)) -> dict
### Description: Retrieves manual NAT rules for a specific policy by its ID.
### Arguments:
### - parent_id (str): ID of the manual NAT policy.
###- token (str): Authentication token obtained from FDM API.

### Function Signature for creating a manual NAT rule
create_nat_rule(parent_id: str, nat_rule_data: dict, token: str = Depends(get_token)) -> dict
### Description: Creates a new manual NAT rule.
### Arguments:
### - parent_id (str): ID of the manual NAT policy.
### - nat_rule_data (dict): JSON containing manual NAT rule data.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for deleting a manual NAT rule
delete_nat_rule(parent_id: str, object_id: str, token: str = Depends(get_token)) -> dict
### Description: Deletes a manual NAT rule by its ID.
### Arguments:
### - parent_id (str): ID of the manual NAT policy.
### - object_id (str): ID of the manual NAT rule to be deleted.
### - token (str): Authentication token obtained from FDM API.

### Function Signature for updating a manual NAT rule
update_nat_rule(parent_id: str, object_id: str, nat_rule_data: dict, token: str = Depends(get_token)) -> dict
### Description: Updates a manual NAT rule by its ID.
### Arguments:
### - parent_id (str): ID of the manual NAT policy.
### - object_id (str): ID of the manual NAT rule to be updated.
### - nat_rule_data (dict): JSON containing updated manual NAT rule data.
### - token (str): Authentication token obtained from FDM API.

## Examples

### Example 1: Retrieving Authentication Token:

token = get_token()

print(f"Authentication Token: {token}")


### Example 2: Creating a Network Object:

network_data = {

    "name": "Office_Network",
    
    "subnet": "192.168.1.0/24"
    
}

response = create_network_object(network_data)

print(f"Created Network Object: {response}")


### Example 3: Deleting a Network Object:

object_id = "network_object_id_here"

response = delete_network_object(object_id)

print(response)


### Example 4: Updating a Network Object:

object_id = "network_object_id_here"

network_object_data = {

    "name": "Updated_Office_Network",
    
    "subnet": "192.168.1.0/24"
    
}

response = update_network_object(object_id, network_object_data)

print(f"Updated Network Object: {response}")


### Example 5: Retrieving a List of Access Policies:

access_policies = get_access_policies()

print(f"Access Policies: {access_policies}")


Example 6: Retrieving Access Rules for a Specific Policy:

policy_id = "policy_id_here"

access_rules = get_access_rules(policy_id)

print(f"Access Rules for Policy {policy_id}: {access_rules}")


### Example 7: Creating an Access Rule

policy_id = "policy_id_here"

access_rule_data = {

    "name": "Allow_HTTP",
    
    "sourceNetworks": ["192.168.1.0/24"],
    
    "destinationNetworks": ["0.0.0.0/0"],
    
    "services": ["HTTP"],
    
    "action": "ALLOW"
}

response = create_access_rule(policy_id, access_rule_data)

print(f"Created Access Rule: {response}")


### Example 8: Deleting an Access Rule:

policy_id = "policy_id_here"

object_id = "access_rule_id_here"

response = delete_access_rule(policy_id, object_id)

print(response)


### Example 9: Updating an Access Rule:

parent_id = "policy_id_here"

object_id = "access_rule_id_here"

access_rule_data = {

    "name": "Updated_HTTP_Rule",
    
    "sourceNetworks": ["192.168.1.0/24"],
    
    "destinationNetworks": ["0.0.0.0/0"],
    
    "services": ["HTTP"],
    
    "action": "ALLOW"
}

response = update_access_rule(parent_id, object_id, access_rule_data)

print(f"Updated Access Rule: {response}")













