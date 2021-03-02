# Youth Activism App (EDF)

## Getting Started

Clone Repo

```
git clone https://github.com/te68/edf-dfg
```

Install packages

```
cd edf-dfg && npm install
```

Run back-end and front-end servers

```
npm run dev
```

## API Docs

- ## Authentication:

### **Register User**

```
  POST http://localhost:3000/api/users
```

Headers:
| Key | Value |
| ------ | ------ |
| Content-Type | application/json |

#### Body:

```
{
"name":"John Smith",
"email":"johnsmith@example.com",
"password":"StrongPassword"
}
```

#### Response:

```
{
 "token":"token"
}
```

---

### **Login User**

```
  POST http://localhost:3000/api/auth
```

#### Headers:

| Key          | Value            |
| ------------ | ---------------- |
| Content-Type | application/json |
| x-auth-token | token            |

#### Body:

```
{
"email":"johnsmith@example.com",
"password":"Yourpassword"
}
```

#### Response:

```
{
 "token":"token"
}
```

---

### **Get Auth User**

```
  GET http://localhost:3000/api/auth
```

#### Headers:

| Key          | Value            |
| ------------ | ---------------- |
| Content-Type | application/json |
| x-auth-token | token            |

#### Body:

```
{
"email":"johnsmith@example.com",
"password":"Yourpassword"
}
```

#### Response:

```
{
 "_id":"mongoDB ID",
 "name":"John Smith",
 "email":"johnsmith@example.com",
 "avatar":"avatar link",
 "date": "2021-02-02T02:52:59.987Z"
}
```

---

- ## Content:

### **Create Content**

```
  POST http://localhost:3000/api/content
```

Headers:
| Key | Value |
| ------------ | ---------------- |
| Content-Type | application/json |
| x-auth-token | token |

#### Body:

```
{
  "title": "Sample Content",
  "url": "https://www.edf.org/",
  "preview": "This is a content of the type article",
  "author": "EDF",
  "contentType": "Article",
  "categories": ["Advice", "Learning"]
}
```

#### Response:

```
{
    "message": "Content created",
    "content": {
        "categories": [
            "Advice",
            "Learning"
        ],
        "_id": "603c189e657e5b102029a637",
        "title": "Sample Content",
        "url": "https://www.edf.org/",
        "preview": "This is a content of the type article",
        "author": "EDF",
        "contentType": "Article",
        "likes": 0,
        "celebrates": 0,
        "dislikes": 0,
        "createdAt": "2021-02-28T22:26:38.145Z",
        "updatedAt": "2021-02-28T22:26:38.145Z",
        "__v": 0
    }
}
```

---

### **Get Content**

```
  GET http://localhost:3000/api/content
```

#### Headers:

| Key          | Value            |
| ------------ | ---------------- |
| Content-Type | application/json |
| x-auth-token | token            |

#### Response:

```
{
    "content": [
        {
            "categories": [
                "Advice",
                "Learning"
            ],
            "_id": "603c189e657e5b102029a637",
            "title": "Sample Content",
            "url": "https://www.edf.org/",
            "preview": "This is a content of the type article",
            "author": "EDF",
            "contentType": "Article",
            "likes": 0,
            "celebrates": 0,
            "dislikes": 0,
            "createdAt": "2021-02-28T22:26:38.145Z",
            "updatedAt": "2021-02-28T22:26:38.145Z",
            "__v": 0
        }
    ],
    "totalCount": 1,
    "totalPages": 1
}}
```

---

### **Update Content**

```
  PUT http://localhost:3000/api/content/<contentId>
```

Headers:
| Key | Value |
| ------------ | ---------------- |
| Content-Type | application/json |
| x-auth-token | token |

#### Body:

```
{
  "title": "Sample Content (updated)",
  "url": "https://www.edf.org/",
  "preview": "This is a content of the type article",
  "author": "EDF",
  "contentType": "Article",
  "categories": ["Advice", "Learning"],
  "likes": 1,
  "celebrates": 5,
  "dislikes": 0
}
```

#### Response:

```
{
    "message": "Content Updated",
    "content": {
        "categories": [
            "Advice",
            "Learning"
        ],
        "_id": "603c189e657e5b102029a637",
        "title": "Sample Content (updated)",
        "url": "https://www.edf.org/",
        "preview": "This is a content of the type article",
        "author": "EDF",
        "contentType": "Article",
        "likes": 0,
        "celebrates": 0,
        "dislikes": 0,
        "createdAt": "2021-02-28T22:26:38.145Z",
        "updatedAt": "2021-02-28T22:37:50.985Z",
        "__v": 0
    }
}
```

---

### **Delete Content**

```
  DELETE http://localhost:3000/api/content/<contentId>
```

Headers:
| Key | Value |
| ------------ | ---------------- |
| Content-Type | application/json |
| x-auth-token | token |

#### Response:

```
{
    "message": "Content Deleted",
}
```

---

### **Get Content Details**

```
  GET http://localhost:3000/api/content/<contentId>
```

Headers:
| Key | Value |
| ------------ | ---------------- |
| Content-Type | application/json |
| x-auth-token | token |

#### Response:

```
{
    "categories": [
        "Advice",
        "Learning"
    ],
    "_id": "603c28969522d38b3471aae1",
    "title": "Sample Content",
    "url": "https://www.edf.org/",
    "preview": "This is a content of the type article",
    "author": "EDF",
    "contentType": "Article",
    "likes": 0,
    "celebrates": 0,
    "dislikes": 0,
    "createdAt": "2021-02-28T23:34:46.126Z",
    "updatedAt": "2021-02-28T23:34:46.126Z",
    "__v": 0
}
```

---

- ## Event:

### **Create Event**

```
  POST http://localhost:3000/api/event
```

Headers:
| Key | Value |
| ------------ | ---------------- |
| Content-Type | application/json |
| x-auth-token | token |

#### Body:

```
{
  "title": "sample event",
  "date": "2022-05-05",
  "time": "5-6pm EST",
  "address": "Random Address",
  "description": "sample event abcde",
  "categories": ["Food Justice"]
}
```

#### Response:

```
{
    "message": "Event created",
    "event": {
        "categories": [
            "Food Justice"
        ],
        "_id": "603c262594940f7ff865b2c4",
        "title": "sample event",
        "date": "2022-05-05T00:00:00.000Z",
        "time": "5-6pm EST",
        "address": "Random Address",
        "description": "sample event abcde",
        "createdAt": "2021-02-28T23:24:21.970Z",
        "updatedAt": "2021-02-28T23:24:21.970Z",
        "__v": 0
    }
}
```

---

### **Get Events**

```
  GET http://localhost:3000/api/event
```

#### Headers:

| Key          | Value            |
| ------------ | ---------------- |
| Content-Type | application/json |
| x-auth-token | token            |

#### Response:

```
{
    "events": [
        {
            "categories": [
                "Food Justice"
            ],
            "_id": "603c262594940f7ff865b2c4",
            "title": "sample event",
            "date": "2022-05-05T00:00:00.000Z",
            "time": "5-6pm EST",
            "address": "Random Address",
            "description": "sample event abcde",
            "createdAt": "2021-02-28T23:24:21.970Z",
            "updatedAt": "2021-02-28T23:24:21.970Z",
            "__v": 0
        }
    ],
    "totalCount": 1,
    "totalPages": 1
}
```

---

### **Update Event**

```
  PUT http://localhost:3000/api/event/<eventId>
```

Headers:
| Key | Value |
| ------------ | ---------------- |
| Content-Type | application/json |
| x-auth-token | token |

#### Body:

```
{
  "title": "sample event (updated)",
  "date": "2022-05-05",
  "time": "5-6pm EST",
  "address": "New Address",
  "description": "sample event abcde",
  "categories": ["Food Justice"]
}
```

#### Response:

```
{
    "message": "Event updated",
    "event": {
        "categories": [
            "Food Justice"
        ],
        "_id": "603c262594940f7ff865b2c4",
        "title": "sample event (updated)",
        "date": "2022-05-05T00:00:00.000Z",
        "time": "5-6pm EST",
        "address": "New Address",
        "description": "sample event abcde",
        "createdAt": "2021-02-28T23:24:21.970Z",
        "updatedAt": "2021-02-28T23:28:11.310Z",
        "__v": 0
    }
}
```

---

### **Delete Event**

```
  DELETE http://localhost:3000/api/event/<eventId>
```

Headers:
| Key | Value |
| ------------ | ---------------- |
| Content-Type | application/json |
| x-auth-token | token |

#### Response:

```
{
    "message": "Event deleted",
}
```

---

### **Get Content Details**

```
  GET http://localhost:3000/api/content/<contentId>
```

Headers:
| Key | Value |
| ------------ | ---------------- |
| Content-Type | application/json |
| x-auth-token | token |

#### Response:

```
{
    "categories": [
        "Food Justice"
    ],
    "_id": "603c262594940f7ff865b2c4",
    "title": "sample event (updated)",
    "date": "2022-05-05T00:00:00.000Z",
    "time": "5-6pm EST",
    "address": "New Address",
    "description": "sample event abcde",
    "createdAt": "2021-02-28T23:24:21.970Z",
    "updatedAt": "2021-02-28T23:28:11.310Z",
    "__v": 0
}
```

---
