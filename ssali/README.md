# Build-a-GraphQL-API-with-Graphene-SQLAlchemy-And-Flask
This is code for a live stream where I walked through how to build a GraphQL API with Flask , SQLAlchemy and Graphene-Python

## To run this code
- Install the project requirements with 
 ```
 pip install -r requirements.txt 
 ```  

- Then created the DB
 ```
 python create_db.py
 ```

 - Finally run with  
 ```
 python main.py
 ```

## Query examples
```
 
query usuarios{
  allUsers{
    pageInfo{
      hasNextPage,
      hasPreviousPage
    },
    edges{
      node{
        id,
        username,
        email
      },
      cursor
    }
  }
}
```

```

query usuarios_y_posts{
  allUsers{
    pageInfo{
      hasNextPage,
      hasPreviousPage
    },
    edges{
      node{
        id,
        username,
        email,
        posts{
          edges{
            node{
              id,
              title
            }
          }
        }
      },
      cursor
    }
  }
}
```


## Mutation examples
```

mutation crearUsuario{
  mutateUser(
    email: "betovone@gmail.com",
    username: "betovone"
  ){
    user{
      id,
      username,
      email,
      posts{
        pageInfo{
          hasNextPage,
          hasPreviousPage
        },
        edges{
          node{
            id,
            title,
            content
          },
          cursor
        }
      }
    }
  }
}
```

```

mutation crearPost{
  mutatePost(
    content: "Diario deportivo",
    title: "Olé",
    userId: 1
  ){
    post{
      id,
      title
    }
  }
}
```

