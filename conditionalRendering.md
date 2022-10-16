--------------------------------------------------------------
## List and Conditional content
--------------------------------------------------------------

### List rendering:

    const dataItems = [{data:1, name:name1},{data:2, name:name2},{data:3, name:name3},{data:4, name:name4}]

    return (
        {data.map(
            item => <button key={item.data} onClick={item.data}>item.name</button>
        )}
    )

If you use the dynamic values in react and pass an array of elements, like `{[<input />,<input />,<input />]}`, react would render it as the elements showed, so if you map an array to jsx elements and pass it, react would render them like a list
In the map you return the jsx element that you want to map the piece of data
Remember that if it is an arrow function with only one line/step, not putting the {} would automatically return 
`(a, b) => a + b` it's the same as `(a, b) => { return a + b }`

--------------------------------------------------------------

