# loopback-component-meta

Component for [LoopBack](https://loopback.io) that adds a Meta model that can be used to retrieve meta data about the model definitions.

# Installation

Install the module

    $ npm install --save loopback-component-meta
    
Configure the module in `server/component-config.json`

```
{
  "loopback-component-meta": {
    "enableRest": true,
    "filter": [
      "ACL",
      "AccessToken",
      "RoleMapping",
      "Role",
      "User"
    ],
    "acls": [{
      "accessType": "*",
      "principalType": "ROLE",
      "principalId": "$unauthenticated",
      "permission": "ALLOW"
    }]
  }
}
```


# Usage

After installation you should be able to retrieve data about your models through the `Meta` endpoint on your API:

## Retrieve all models:

[http://0.0.0.0:3000/api/Meta](http://0.0.0.0:3000/api/Meta)


```
[{
	id: "Category",
	name: "Category",
	properties: {
		name: {
			type: "String",
			required: true
		}
	},
	acls: [],
	base: "BaseModel",
	idInjection: true,
	methods: {},
	mixins: {
		ModifiedTimestamp: {}
	},
	relations: {
		products: {
			type: "hasMany",
			model: "Product",
			foreignKey: ""
		}
	},
	strict: false,
	validations: []
}, {
	id: "Product",
	name: "Product",
	properties: {
		name: {
			type: "String",
			required: true
		}
	},
	acls: [],
	base: "BaseModel",
	idInjection: true,
	methods: {},
	mixins: {
		ModifiedTimestamp: {}
	},
	relations: {
		category: {
			type: "belongsTo",
			model: "Category",
			foreignKey: ""
		}
	},
	strict: false,
	validations: []
}]
```


## Retrieve one model:


[http://0.0.0.0:3000/api/Meta/Category](http://0.0.0.0:3000/api/Meta/Category)

```
{
	id: "Category",
	name: "Category",
	properties: {
		name: {
			type: "String",
			required: true
		}
	},
	acls: [],
	base: "BaseModel",
	idInjection: true,
	methods: {},
	mixins: {
		ModifiedTimestamp: {}
	},
	relations: {
		products: {
			type: "hasMany",
			model: "Product",
			foreignKey: ""
		}
	},
	strict: false,
	validations: []
}
```
