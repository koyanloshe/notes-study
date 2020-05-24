# Declarative vs imperative

## Imperative

`const toLowerCase = input => { `
`    const output = [];`
`    `
`    for (let i = 0; i < input.length; i++) { `
`      output.push(input[i].toLowerCase());`
`    } `
`    `
`    return output;`
`};`

## Declarative

`const toLowerCase = input => input.map(value => value.toLowerCase());`

In declarative programming, developers only describe what they want to achieve, and there’s no need to list all the steps to make it work.

React = declarative

