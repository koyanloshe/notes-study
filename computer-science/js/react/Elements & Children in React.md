# Elements & Children in React

  { 
	type: Title, 
	props: { 
		color: 'red', 
		children: { 
			type: 'h1', 
			props: { 
				children: 'Hello, H1!' 
        			} 
      		} 
    	} 
  }

The type of an element is important as it tells React how to deal with the element itself. If the type is a string, the element is a DOM node while if the type is a function, the element is a component

React DOM and React Native use reconciliation - when the type of the element is a function, React calls it, passing the props to get back the underlying elements. It keeps performing the same operation recursively on the result until it gets a tree of DOM nodes that React can render on the screen.

