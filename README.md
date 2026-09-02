# User API — Automated Test Suite with Postman

Automated tests written with Postman for the **Nord-s User API** (`https://app.swaggerhub.com/apis-docs/nord-s/User-API/1.0.0`). The API lets user to log in, retrieve and create items.

## Files
| File | Purpose |
|------|---------|
| `User API.postman_collection.json` | Tests collection. |
| `User API.postman_environment.json` | Environment: `base_url`, `user_token`, `item_id`, `files_schema`, `fields_schema`. |

## How to run

### Postman (GUI)
1. Import both JSON files.
2. Select the *User API* environment.
3. Run the collection with the Collection Runner.

## Notes

Currently, User API requests always return 200/201 statuses, no failed statuses, but fail statuses and messages are defined in Swagger, so included in this collection under "Fail flows" folders.

## Security risks

- User token should have an expiration time and rotation.
- Secret value (GET fields -> type password -> value) shouldn't be returned on a general item's GET request and should be encrypted (now just base-64 encoded).
- In GET /user/{id}/item request need to make sure that the item id is also checked with the user token - if that item belongs to the authenticated user (to not access any user items with having just item id).
- Looks like a lot of sensitive information fields are returned - need to check if they all are used/required from frontend (like files -> content_path, shares -> user_uuid).