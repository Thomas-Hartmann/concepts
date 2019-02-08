# Graphql
An alternative to rest endpoints
- Rest: `<some host>:port/api/person/32`
- Rest: 
```
        { person { 
            name
            email
          }
        }
```
- Graphql query looks like json without the values.
- The response is actual json.
- Graphql queries are more precise than rest endpoint queries.
   - The response contains only what was asked for.
   - 
- Comments are made with `#`
- Arguments are send with queries on specific fields using `()` with named parameter like: `login:""`
    - Example: 
    ```graphql
    {
      repositoryOwner(login:"Thomas-Hartmann"){
        id
        url
      }
    }
    ```
- Data types (argument and field types)
    - Integer
    - Float
    - String
    - Boolean
    - Null
    - Enum
    - List
    - Object
- Alias
    - When querying same field with more than once with different values one or all can have alias: `<aliasname>: fieldname(arg1:"",arg2:"",...) {}`
- Fragments
    - When certain fields are used repetedly then we can use a fragment insted: `fragment <fragment_name> on <ressource_name> {field1 field1 ...}`
    - Using them in a query: `{...<fragment_name }`
- Nested fields
    - otional arguments: <Resource>(first: number) or last: number or 
### Pros and Cons
- Pros
    - When data is very hierarchical. e.g objects referencing objects and collections etc. 
    - When the same data needs to be selected in many different ways
    - When there is a lot of data and we need just small pieces of it in different usecases
    - Schemas on backend ensures type safety.
- Cons
    - It takes time to write schemas on node server. 
    - You have to do things different.

#### Graphql with java
- To maintain strong typing and intuitive design, it is common to represent GraphQL types with equivalent Java classes, and fields with methods

#### Resources
- [graphql api](https://githubengineering.com/the-github-graphql-api/)
- [graphql explorer](https://developer.github.com/v4/explorer/)
   - Write queries against my github pofile
   - Write queries in left pane and see results in right pane
   - `ctrl+space` when inside the query shows all available fields
   -  
- See example project in `/home/thomas/projects/jsProjects/_node_playground/graphqlDemo`
