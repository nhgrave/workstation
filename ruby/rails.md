# Rails

## Start new project standalone

```bash
rails new project-name --database postgresql --skip-keeps --skip-test
```

## Start new project as API

```bash
rails new project-name --database postgresql --skip-keeps --skip-test --api
```

## Gesnerate a model

```bash
rails generate model User name:string email:string password_digest:string
```

## GEnerate a controll

```bash
rails generate controller Authentication create delete
```
