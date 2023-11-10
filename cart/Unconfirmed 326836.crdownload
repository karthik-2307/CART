import { initializeApp } from "https://www.gstatic.com/firebasejs/9.15.0/firebase-app.js"
import { getDatabase, ref, push , onValue ,remove} from "https://www.gstatic.com/firebasejs/9.15.0/firebase-database.js"
const appsettings=
{
    // databaseurl:
    databaseURL:"https://play-ground-b82b1-default-rtdb.asia-southeast1.firebasedatabase.app/"
}
const app = initializeApp(appsettings)
const database = getDatabase(app)
const shoppingListInDB = ref(database, "shoppingList")
const buttonEl=document.getElementById("add-button");
let shoppingListEl=document.getElementById("shopping-list")
const inputEl=document.getElementById("input-field")
buttonEl.addEventListener("click",function()
{
    let inputvalue=inputEl.value
    push(shoppingListInDB,inputvalue)
    // shoppingListEl.innerHTML+=`<li>${inputvalue}</li>`
    // inputEl.value=""
    inputclear();
    // appenditem(inputvalue);
    console.log(inputvalue)
})
onValue(shoppingListInDB,function(snapshot)
{
//    console.log(snapshot.val)
  if(snapshot.exists())
  {
   let itemsarray=Object.entries(snapshot.val())
   console.log(itemsarray)
   clearshoppinglist()
   for(var i=0;i<itemsarray.length;i++)
   {
    let currentitem=itemsarray[i]
    let currentItemID = currentitem[0]
    let currentItemvalue=currentitem[1]
   appenditem(currentitem)
   }
  }
  else
  {
    shoppingListEl.innerHTML="There are no other..."
  }
})
function clearshoppinglist()
{
    shoppingListEl.innerHTML = ""
}
function inputclear()
{
    inputEl.value=""
}
function appenditem(item)
{
    // shoppingListEl.innerHTML+=`<li>${inputvalue}</li>`
    let item1=item[0]
    let item2=item[1]
    let newitem=document.createElement("li")
    newitem.textContent=item2
    newitem.addEventListener("dblclick",function()
    {
        // console.log(item)
        let deleteitem=ref(database,`shoppingList/${item1}`)
        console.log(deleteitem)
        remove(deleteitem)
    })
    shoppingListEl.append(newitem)
}