---
layout: default
title: Security - Access Control
nav_order: 21
has_children: true
has_toc: false
---

# Access control

After you [configure the Security plugin](../security-configuration/) to use your own certificates and preferred authentication backend, you can start adding users, creating roles, and mapping roles to users.

This section of the documentation covers what a user is allowed to see and do after successfully authenticating.


## Concepts

Term | Description
:--- | :---
Permission | An individual action, such as creating an index (e.g. `indices:admin/create`). For a complete list, see [Permissions](permissions/).
Action group | A set of permissions. For example, the predefined `SEARCH` action group authorizes roles to use the `_search` and `_msearch` APIs.
Role | Security roles define the scope of a permission or action group: cluster, index, document, or field. For example, a role named `delivery_analyst` might have no cluster permissions, the `READ` action group for all indices that match the `delivery-data-*` pattern, access to all document types within those indices, and access to all fields except `delivery_driver_name`.
Backend role | (Optional) Additional, external roles that come from an authorization backend (e.g. LDAP/Active Directory).
User | Users make requests to Elasticsearch clusters. A user has credentials (e.g. a username and password), zero or more backend roles, and zero or more custom attributes.
Role mapping | Users assume roles after they successfully authenticate. Role mappings, well, map roles to users (or backend roles). For example, a mapping of `kibana_user` (role) to `jdoe` (user) means that John Doe gains all the permissions of `kibana_user` after authenticating. Likewise, a mapping of `all_access` (role) to `admin` (backend role) means that any user with the backend role of `admin` (from an LDAP/Active Directory server) gains all the permissions of `all_access` after authenticating. You can map each role to many users and/or backend roles.

The Security plugin comes with a number of [predefined action groups](default-action-groups/), roles, mappings, and users. These entities serve as sensible defaults and are good examples of how to use the plugin.
