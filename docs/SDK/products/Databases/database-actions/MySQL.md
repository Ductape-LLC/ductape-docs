---
sidebar_position: 2
---

# MySQL Database Actions

| **Action Type** | **SQL Query Type**          |
|------------------|-----------------------------|
| Read             | SELECT                     |
| Create           | INSERT                     |
| Update           | UPDATE                     |
| Delete           | DELETE                     |
| Aggregate        | SELECT (for aggregations)  |

---

## Creating MySQL Database Actions

### Create Operation

```typescript
const data: IProductDatabaseAction = {
  tag: 'mysql-db-tag:create-user',
  tableName: 'users',
  type: DatabaseActionTypes.CREATE,
  template: `
    INSERT INTO users (username, firstname, lastname, date_of_birth, address, occupation)
    VALUES ('{{username}}', '{{firstname}}', '{{lastname}}', '{{dateOfBirth}}', '{{address}}', '{{occupation}}')
  `
};

const action = await product.createDatabaseAction(data);
```

### Read Operation

```typescript
const data: IProductDatabaseAction = {
  tag: 'mysql-db-tag:read-user',
  tableName: 'users',
  type: DatabaseActionTypes.READ,
  template: `
    SELECT * FROM users WHERE username = '{{username}}'
  `
};

const action = await product.createDatabaseAction(data);
```

### Update Operation

```typescript
const data: IProductDatabaseAction = {
  tag: 'mysql-db-tag:update-user',
  tableName: 'users',
  type: DatabaseActionTypes.UPDATE,
  template: `
    UPDATE users
    SET firstname = '{{firstname}}', lastname = '{{lastname}}', address = '{{address}}'
    WHERE username = '{{username}}'
  `
};

const action = await product.createDatabaseAction(data);
```

### Delete Operation

```typescript
const data: IProductDatabaseAction = {
  tag: 'mysql-db-tag:delete-user',
  tableName: 'users',
  type: DatabaseActionTypes.DELETE,
  template: `
    DELETE FROM users WHERE username = '{{username}}'
  `
};

const action = await product.createDatabaseAction(data);
```