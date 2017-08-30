# Top-down data flow and debugging

Some helpful points on debugging follow from the cascading nature of data in React:

* If the props and state are correct, all you need to check is render() or the functions it calls

* If the state is wrong, check the setState() calls

* If the props are wrong, check the parent components that passed those props down 
