---
title: Idea Box

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Ideabox is a simple application that allows users to create a pool of ideas and promote collaboration. It has the following features:

- Create an account
- Log in a registered user
- Reset Password
- Edit user profile
- Create Ideas
- Edit Ideas
- Delete Ideas
- Comment on Ideas
- Reset password email
- Search for Ideas
- Filter ideas by category

# Authentication

## Register

> Request Body:

```javascript

{
  "username": "kolawole",
  "email": "kolawole@gmail.com",
  "password": "kolawole12334"
}

```

> Sample Response:

```javascript
{
  "message": "Sign up successful",
  "success": true,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbiI6eyJ1c2VyIjp7Il9pZCI6IjVhMzI1NDQ4MTYyZGMzMDAyYzk1NjcyYyIsInVzZXJuYW1lIjoiT2xhd2FsZSIsInBhc3N3b3JkIjoiJDJhJDEwJHQ1LlI5ZnJXR1FOMXZYMXdOUGR6N095VXlmczBlZkxCeXZJSE9kRmpldHNGLlkxaEZJaHNlIiwiZW1haWwiOiJzaG9sYUBnbWFpbC5jb20iLCJfX3YiOjAsInVwZGF0ZWRBdCI6IjIwMTctMTItMTRUMTA6MzY6NTYuNjgyWiIsImNyZWF0ZWRBdCI6IjIwMTctMTItMTRUMTA6MzY6NTYuNjgxWiJ9fSwiaWF0IjoxNTEzMjQ3ODg3LCJleHAiOjE1MTMzMzQyODd9.3SZX6RAWqky4Nuj7qtzh-fg7vMxIBggnS0E4tmmgfWk",
  "userDetails": {
    "email": "kolawole@gmail.com",
    "username": "kolawole",
    "password": "kolawole12334"
  }
}

```

### HTTP Request

`POST /api/v1/users/signup`

This endpoint registers a new user

`onSuccess - Status Code [201]`

`onError - Status Code [400, 409, 500]`

## Log in

> Request Body:

```javascript

{
  "email": "funso@andela.com",
  "password": "Welcome3000#"
}
```

> Sample Response:

```javascript
{
  "message": "Sign in successful",
  "success": true,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbiI6eyJ1c2VyIjp7Il9pZCI6IjVhMzI1NDQ4MTYyZGMzMDAyYzk1NjcyYyIsInVzZXJuYW1lIjoiT2xhd2FsZSIsInBhc3N3b3JkIjoiJDJhJDEwJHQ1LlI5ZnJXR1FOMXZYMXdOUGR6N095VXlmczBlZkxCeXZJSE9kRmpldHNGLlkxaEZJaHNlIiwiZW1haWwiOiJzaG9sYUBnbWFpbC5jb20iLCJfX3YiOjAsInVwZGF0ZWRBdCI6IjIwMTctMTItMTRUMTA6MzY6NTYuNjgyWiIsImNyZWF0ZWRBdCI6IjIwMTctMTItMTRUMTA6MzY6NTYuNjgxWiJ9fSwiaWF0IjoxNTEzMjQ3ODg3LCJleHAiOjE1MTMzMzQyODd9.3SZX6RAWqky4Nuj7qtzh-fg7vMxIBggnS0E4tmmgfWk",
  "userDetails": {
    "email": "funso@andela.com",
    "username": "Qudus Kunle"
  }
}
```

### HTTP Request

`POST /api/v1/users/signin`

This endpoint verifies if a user is registered and then logs the user if verified or throws the appropriate error if not verified. You can login with email and password

`onSuccess - Status Code [200]`

`onError - Status Code [400, 401, 404, 500]`


## Update Profile

> Request Body:

```javascript

{
  "username": "funsho",
  "email": "funso@andela.com",
}

```

> Sample Response:

```javascript
{
  "message": "Profile updated successfully",
  "success": true,
  "user": {
    "username": "funsho",
    "email": "funso@andela.com"
  }
}
```

### HTTP Request

`PUT - /api/v1/users/profiles`

This endpoint updates a user profile

`onSuccess - Status Code [200]`

`onError - Status Code [400, 401, 404, 500]`


## Reset Password

> Request Body:

```javascript

{
  "email": "kolawole@andela.com",
}

```

> Sample Response:

```javascript
{
  "message": "Reset password email sent successfully",
  "success": true
}
```

### HTTP Request

`POST - /api/v1/users/passwords`

This endpoint generates a hash token and sends a reset link to the user via email

`onSuccess - Status Code [200]`

`onError - Status Code [400, 404, 500]`


## Update password

> Request Body:

```javascript

{
  "newPassword": "12345678",
  "confirmPassword": "12345678"
}

```

> Sample Response:

```javascript
{
  "message": "Password has been updated",
  "success": true
}
```

### HTTP Request

`PUT /api/v1/users/passwords/:hash`

Upon reception of an email to reset password, this method receives the new password entered by the user and replaces the user's old password with the new one

`onSuccess - Status Code [200]`

`onError - Status Code [400, 404, 500, 503]`


## Create an Idea

```javascript
{
  "title": 'In the Light of Truth',
  "description": 'The Grail Message',
  "category": 'AbdruShin',
  "access": 'public'
}
```

> Sample Response:

```javascript
{
    "message": 'Your Idea has been created successfully',
    "success": true,
    "createdIdea": {
      "title": 'In the Light of Truth',
      "description": 'The Grail Message',
      "category": 'AbdruShin',
      "access": 'public'
    }
  }
```

### HTTP Request

`POST /api/v1/users/idea`

This endpoint creates a new idea.

`onSuccess - Status Code [201]`

`onError - Status Code [400, 401, 409, 500]`


## Public ideas

> Sample Response:

```json
{
  "ideas":
    [
      {
        "_id": "5a2237e61f7c9a0bad4e3206",
        "title": "Ok, morning here",
        "description": "This is to demonstrate how to bake cake for the young ones",
        "__v": 0,
        "createdAt": "2017-12-02T05:19:34.811Z",
        "updatedAt": "2017-12-02T05:19:34.811Z",
        "author": {
          "id": "5a2085505d1e9a42bece8858",
          "name": "Quduskunle"
        },
        "status": false,
        "access": [
          "Public"
        ],
        "category": [
          "Cosmetics"
        ]
      },
      {
        "_id": "5a25599874dea07c3fffcdcb",
        "title": "Abdrushin",
        "description": "The Book of Grail",
        "__v": 0,
        "createdAt": "2017-12-04T14:20:08.632Z",
        "updatedAt": "2017-12-04T14:20:08.632Z",
        "author": {
          "id": "5a25589374dea07c3fffcdca",
          "name": "Quduskunle"
        },
        "status": false,
        "access": [
          "Public"
        ],
        "category": [
          "Religion"
        ]
      }
    ],
    pageInfo: {
      page: 1,
      pageCount: 4,
      pageSize: 6,
      count: 21
    }
  }
}
```

### HTTP Request

`GET /api/v1/users/ideas/public`

This endpoint fetch all public ideas.

`onSuccess - Status Code [201]`

`onError - Status Code [400, 401, 409, 500]`


## Fetch Idea

> sample response:

```json
{
  ideas: [
    {
      _id: "5a3238758e67dc4644a9d4ce",
      title: "New Idea",
      description: "**Yes Nes Idea**",
      __v: 0,
      createdAt: "2017-12-14T08:38:13.674Z",
      updatedAt: "2017-12-14T08:38:13.674Z",
      author: {
        id: "5a284ddbedc9b460093101af",
        name: "Joke Adunni"
      },
      status: false,
      access: [
        "Public"
      ],
      category: [
        "Technology"
      ]
    }
  ]
}
```

### HTTP Request

`GET /api/v1/users/ideas/<ID>`

This endpoint retrieves a specific idea.

`onSuccess - Status Code [200]`

`onError - Status Code [400, 404, 500]`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| ID        | The ID of the idea to fetch |


## Delete an idea

> Response:

```json
{
  success: true,
  message: "Idea deleted successfully"
}
```
### HTTP Request

`DELETE api/v1/users/ideas/<ID>`

This endpoint deletes an idea.

`onSuccess - Status Code [200]`

`onError - Status Code [400, 404, 500]`

### URL Parameters

| Parameter | Description                  |
| --------- | ---------------------------- |
| ID        | The ID of the idea to delete |
