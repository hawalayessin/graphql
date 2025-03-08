# TP3 : Système de Gestion de Tâches avec GraphQL


## Description
Ce projet est une API GraphQL permettant de gérer des tâches avec un serveur Apollo, Node.js et Express. Il permet d'ajouter, modifier, supprimer et marquer des tâches comme complètes.

## Prérequis
- [Node.js](https://nodejs.org/) (v14+)
- [npm](https://www.npmjs.com/) ou [yarn](https://yarnpkg.com/)

## Installation

1. **Cloner le projet** :
   ```bash
   git clone https://github.com/hawalayessin/graphql.git
   cd graphql
   ```
2. **Installer les dépendances** :
   ```bash
   npm install
   ```

## Structure du projet
```
/graphql
├── taskSchema.gql  # Schéma GraphQL
├── taskSchema.js   # Importation du schéma
├── taskResolver.js # Résolveurs GraphQL
├── index.js        # Serveur Express et Apollo
└── README.md       # Documentation
```

## Lancement du serveur

Démarrer l'API GraphQL :
```bash
node index.js
```
Le serveur sera disponible sur : [http://localhost:5000/graphql](http://localhost:5000/graphql)

## Schéma GraphQL
### **Types**
```graphql
type Task {
  id: ID!
  title: String!
  description: String!
  completed: Boolean!
  duration: Int!
}

type Query {
  task(id: ID!): Task
  tasks: [Task]
}

type Mutation {
  addTask(title: String!, description: String!, completed: Boolean!, duration: Int!): Task
  completeTask(id: ID!): Task
  changeDescription(id: ID!, description: String!): Task
  deleteTask(id: ID!): Task
}
```

## Requêtes GraphQL

### **1. Récupérer toutes les tâches**
```graphql
query {
  tasks {
    id
    title
    description
    completed
    duration
  }
}
```

### **2. Ajouter une nouvelle tâche**
```graphql
mutation {
  addTask(title: "Nouvelle tâche", description: "Détails de la tâche", completed: false, duration: 60) {
    id
    title
  }
}
```

### **3. Marquer une tâche comme terminée**
```graphql
mutation {
  completeTask(id: "1") {
    id
    completed
  }
}
```

### **4. Modifier la description d'une tâche**
```graphql
mutation {
  changeDescription(id: "1", description: "Nouvelle description") {
    id
    description
  }
}
```

### **5. Supprimer une tâche**
```graphql
mutation {
  deleteTask(id: "2") {
    id
  }
}
```


