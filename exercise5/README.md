# Exercise 5

Fix the [urls.py](https://github.com/Speedy1991/strawberry-workshop/blob/master/core/urls.py#L2): `exercise5.schema.schema`

## Interfaces

Let's write our first interface. For less boilerplate I added a `socialClub(pk: Int)` field

## TODO

- [query.py](https://github.com/Speedy1991/strawberry-workshop/blob/master/exercise5/schema/types.py)
- [schema.py](https://github.com/Speedy1991/strawberry-workshop/blob/master/exercise5/schema/schema.py)


## Sample

Query:
```
query SocialClub {
  socialClub(pk: 5) {
    id
    name
    persons {
      id
      __typename
      firstName
      lastName
      socialClub {
        id
        name
      }
      ... on MemberType {
        takenAmount
      }
      ... on GuestType {
        seedCount
      }
    }
  }
}
```

Result:
Look out for the fields `takenAmount`,  `seedCount` and `__typename` 

# Question:
Why could it be important to query the `__typename` in the interface? Think about autogenerated schemas for e.g. typescript