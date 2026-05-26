# IntelliJ Platform MCP Database

Source: https://www.jetbrains.com/help/idea/mcp-server.html

Use this for database connections, schemas, objects, queries, previews, and cancellation exposed by official MCP.

## Scope

- Use database MCP tools only when the IDE has configured data sources.
- Do not use database tools for DDL data sources without an underlying DBMS connection.
- Prefer read-only operations unless the user explicitly asks for mutations.
- Ask before running data-changing SQL.

## Connections And Metadata

- Use connection-list tools to discover configured connections.
- Use `test_database_connection` when connection health matters.
- Use schema and object-listing tools before guessing table names.
- Use object details tools for columns, indexes, constraints, and object definitions when available.

## Query Work

- Use recent-query tools to recover IDE SQL context.
- Use query execution tools only with a clear connection id and SQL text.
- Use preview tools for safe sampling of table or view contents.
- Summarize large results.
- Avoid exposing secrets from connection strings, parameters, or result data.

## Cancellation

- Use cancellation tools only for a specific known query/session.
- Confirm intent before cancelling a query when ownership is unclear.
- Report cancellation as requested, not as guaranteed rollback.
