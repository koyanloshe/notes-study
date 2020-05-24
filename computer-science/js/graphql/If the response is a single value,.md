## If the response is a single value,

 
`post(`*`parent`*`, `*`args`*`, `*`ctx`*`, `*`info`*`){`
`return posts.find((`*`post`*`)=>{`
`return post.id === parent.post`
`})`
`}`
` `
` `
`If the response is an array,`
`posts(`*`parent`*`, `*`args`*`, `*`ctx`*`, `*`info`*`){`
`return posts.filter((`*`post`*`)=>{`
`return post.author === parent.id;`
`})`
`}`

**## Create
**## 

##  

## Schema: 

`createUser(name: String!, email: String!, age: Int): User!`
##  

## Resolver:

`createComment(`*`parent`*`, `*`args`*`, `*`ctx`*`, `*`info`*`){`
`const userExists = users.some((`*`user`*`)=> user.id === args.author)`
`const postExists = posts.some((`*`post`*`)=> post.id === args.post && post.published)`
`if(!postExists || !userExists){`
`throw `**`new `***`Error`*` ('Problem creating comment')`
`}`
`const comment = {`
`id: uuidv4(),`
`...args`
`}`
`comments.push(comment)`
`return comment`
`}`
##  

##  

## …args is a spread operator with Babel dependency

`npm install babel-plugin-transform-object-rest-spread`

**# Delete
**# 

#  

# Schema:

`deleteUser(id: ID!):User!`
##  

# Resolver:

`deleteUser(`*`parent`*`, `*`args`*`, `*`ctx`*`, `*`info`*`){`
`const userIndex = users.findIndex((`*`user`*`)=> user.id===args.id)`
`if (userIndex === -1){`
`throw `**`new `***`Error`*`('User not found')`
`}`
`const deletedUsers = users.splice(userIndex,1)`
`posts = posts.filter((`*`post`*`)=>{`
`const match = post.author === args.id`
`if(match){`
`comments = comments.filter((`*`comment`*`)=> comment.post !== post.id)`
`}`
`return !match`
`})`
`comments = comments.filter((`*`comment`*`)=> comment.author !== args.id)`
`return deletedUsers[0]`
## }

#  

