# Arrays

## Initializing array

```javascript
const emptyArray = []; // []
const hardCodedArray = [1, 2, 3] // [1, 2, 3]
const arrayFill = Array(3).fill() // [undefined, undefined, undefined]
```

{% hint style="info" %}
The `arrayFill` is a great alternative to make fake seeders and I use mostly on ReactJS to repeat a component based on something length.
{% endhint %}

```javascript
/**
 * Seeder example
 * Get a random date on actual month
 */
const dates = Array.from(new Array(50)).map(() => {
    const firstDay = dayjs().startOf("month").toDate()
    const lastDay = dayjs().endOf("month").toDate();
    return dayjs(faker.date.between(firstDay, lastDay));
});

/**
 * React example
 * Repeat the paginate number component based on numberOfPages
 * from API response
 */
Array(users.numberOfPages).fill().map((_, index) => 
    <PaginateNumber number={index} />
)


```

## Iterating

#### Simple iterating

```javascript
const users = []
/**
 * For I
 */ 
for (let i = 0; i < users.length; i++) {}

/**
 * For of (nice sintax, but bad perfomance)  
 * But is what I mostly use, prefer this than Array.forEach
 */
for (let user of users) {}

/**
 * For in (only for objects) 
 */ 
const user = { name: "Miguel", birthday: "28/05/1996" }

for (let userKeys of user) {
    console.log(userKeys) // logs "name" and "birthday"
}
```

**Async iterating**

```javascript
/**
 * It's calling a await in every iteration
 */
async function asyncIterate() {
    const promises = [
      User.findAll(),
      Roles.findAll(),
    ]
    
    for await (let promise of promises) {
      console.log(promise)
    }
    // logs:
    // Array of users
    // Array of roles
}

```

