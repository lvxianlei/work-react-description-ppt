## 或者这样
```
import React, { useState, PureComponent } from "react";
//PureComponent
class DropTargetBox extends PureComponent {
    constructor(props) {
        super(props);
        this.state = {
            page: props.page,
            list: props.page.get('pageFieldPositions').filter(item => item.name !== 'id'),
            highlighted: props.canDrop,
            hovered: props.isOver,
        }
        this.onSortEnd = this.onSortEnd.bind(this);
        this.addListItem = this.addListItem.bind(this);
    }
    onSortEnd({ oldIndex, newIndex }) {
        this.setState({ list: arrayMove(this.state.list, oldIndex, newIndex) });
    }
    componentWillReceiveProps(nextProps) {
        !is(nextProps.page, this.state.page) && this.setState({
            page: nextProps.page,
            list: nextProps.page.get('pageFieldPositions').filter(item => item.name !== 'id'),
            hovered: nextProps.isOver
        })
    }
    addListItem(itemData) {
        const list = this.state.list.slice(0);
        this.setState({ list: list.concat([itemData]) });
    }
    render() {
        const { connectDropTarget, pages } = this.props;
        const { hovered, list } = this.state;
        return connectDropTarget(<nav className="dropTarget">
            <div className={hovered ? "hover" : "hide"}>
                <p>新增配置项</p>
            </div>
            <SortableList onSortEnd={this.onSortEnd} axis="xy" >
                {
                    list.map((item, index) => <SortableItem index={index} key={index} data={item} pages={pages} />)
                }
            </SortableList>
        </nav>)
    }
}
```