# EP.2



{% embed url="https://react.dev/learn/thinking-in-react" %}

## React 예제로 연습해보자!

### 컴포넌트를 나누지 않고  App()에 다 넣은 경우

```typescript
App.tsx

const products = [
	{ category: "Fruits", price: "$1", stocked: true, name: "Apple" },
	{ category: "Fruits", price: "$1", stocked: true, name: "Dragonfruit" },
	{ category: "Fruits", price: "$2", stocked: false, name: "Passionfruit" },
	{ category: "Vegetables", price: "$2", stocked: true, name: "Spinach" },
	{ category: "Vegetables", price: "$4", stocked: false, name: "Pumpkin" },
	{ category: "Vegetables", price: "$1", stocked: true, name: "Peas" }
  ]

export default function App() {

	return (
		<div className='filterable-products-container'>
			<div className='search-bar'>
				<input type="text" placeholder='검색어를 입력하세요' />
			</div>
			<div>
				<input type="checkbox" id='only-stock' />
				<label htmlFor="only-stock">
					Only show Products in stock
				</label>
			</div>
			<table className='product-table'>
				<thead>
					<tr>
						<th>Name</th>
						<th>Price</th>
					</tr>
				</thead>
				<tbody>
					<tr>
						<th colSpan={2}>
							{products[0].category}
						</th>
					</tr>
					{products.map((product)=>{
						return(
							<tr>
								<td>{product.name}</td>
								<td>{product.price}</td>
							</tr>
						)
					})}
				</tbody>
			</table>
		</div>
	);
}
```
