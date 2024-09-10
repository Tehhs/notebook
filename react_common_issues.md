# Children tying to manage their own state 

```jsx

const ChildElement = ({state}) => { 
    const [innerState, setInnerState] = useState(state)

    const _onItemClick = (clickedId) => { 
        const newInnerState = [...innerState]
        newInnerState.find( item => item.id == clickedId)?.selected = true 
    }
    
    return <div>
        {
            state?.map( (item, itemIndex) => 
                <div key={itemIndex} onClick={()=>{_onItemClick(item.id)}}>
                    {item.name} {item.selected == true && "(clicked)"}
                </div>
            )
        }
    </div>
}

const ParentElement = ({state}) => { 
    const [state, setState] = useState([
        {id: 1, name: "John", selected: false},
        {id: 1, name: "Alex", selected: false}
    ])

    return <ChildElement state={state}/>
}

```
