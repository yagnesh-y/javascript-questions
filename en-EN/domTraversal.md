# Dom Traversal

###### getElementById:
An ID should be unique within a page. However, if more than one element with the specified ID exists, the getElementById() method returns the first element in the source code. Returns null if no elements with the specified ID exists.

document.getElementById('idName')

###### getElementsByClassName
document.getElementByClassName('classname')
The getElementsByClassName() method returns a collection of all elements in the document with the specified class name, as a NodeList object.

###### getElementByTagName
document.getElementsByTagname('any tag')
returns a collection of all elements in the document with the specified tag name, as a NodeList object.The parametervalue "*" returns all elements in the document. You can use the length property of the NodeList object to determine the number of elements with the specified tag name, then you can loop through all elements and extract the info you want.

###### getElementsByName
document.getElementsByName('any value of the name attribute')
The getElementsByName() method returns a collection of all elements in the document with the specified name (the value of the name attribute), as a NodeList object.

###### querySelector : returns first occurance
document.querySelector('any html/css selector')
Note: The querySelector() method only returns the first element that matches the specified selectors. To return all the matches, use the querySelectorAll()method instead.If the selector matches an ID in document that is used several times (Note that an "id" should be unique within a page and should not be used more than once), it returns the first matching element.

###### querySelectorAll : returns all occurances
document.querySelectorAll('any html/css selectors')
The querySelectorAll() method returns all elements in the document that matches a specified CSS selector(s), as a static NodeList object.

###### parentNode
The parentNode property returns the parent node of the specified node, as a Node object.
Note: In HTML, the document itself is the parent node of the HTML element, HEAD and BODY are child nodes of the HTML element.
This property is read-only.

```javascript
	var itemList = document.querySelector('#items');
	console.log(itemList.parentNode);
	itemList.parentNode.style.backgroundColor = '#f4f4f4';
	console.log(itemList.parentNode.parentNode.parentNode);
```

##### parentElement
The parentElement property returns the parent element of the specified element.
The difference between parentElement and parentNode, is that parentElement returns null if the parent node is not an element node:

```javascript
document.body.parentNode; // Returns the <html> element
document.body.parentElement; // Returns the <html> element

document.documentElement.parentNode; // Returns the Document node
document.documentElement.parentElement; // Returns null (<html> does not have a parent ELEMENT node)
```

##### previousSibling/previousElementSibling
The previousSibling property returns the previous node of the specified node, in the same tree level.
The returned node is returned as a Node object.
The difference between this property and previousElementSibling, is that previousSibling returns the previous sibling node as an element node, a text node or a comment node, while previousElementSibling returns the previous sibling node as an element node (ignores text and comment nodes).
This property is read-only.

##### nextSibling/nextElementSibling
The nextSibling property returns the node immediately following the specified node, in the same tree level.
The returned node is returned as a Node object.
The difference between this property and nextElementSibling, is that nextSibling returns the next sibling node as an element node, a text node or a comment node, while nextElementSibling returns the next sibling node as an element node (ignores text and comment nodes).

##### childNodes/children
The childNodes property returns a collection of a node's child nodes, as a NodeList object.
The nodes in the collection are sorted as they appear in the source code and can be accessed by index numbers. The index starts at 0.
Note: Whitespace inside elements is considered as text, and text is considered as nodes. Comments are also considered as nodes.
Tip: You can use the length property of the NodeList object to determine the number of child nodes, then you can loop through all child nodes and extract the info you want.
This property is read-only.
Tip: To return a collection of a node's element nodes (excluding text and comment nodes), use the children property.
Tip: element.childNodes[0] will produce the same result as the firstChild property.

##### firstChild/firstElementChild
The firstChild property returns the first child node of the specified node, as a Node object.
The difference between this property and firstElementChild, is that firstChild returns the first child node as an element node, a text node or a comment node (depending on which one's first), while firstElementChild returns the first child node as an element node (ignores text and comment nodes).
Note: Whitespace inside elements is considered as text, and text is considered as nodes (See "More Examples").
This property is read-only.
Tip: Use the element.childNodes property to return any child node of a specified node. childNodes[0] will produce the same result as firstChild.
Tip: To return the last child node of a specified node, use the lastChild property.

##### lastChild/lastElementChild
The lastElementChild property returns the last child element of the specified element.
The difference between this property and lastChild, is that lastChild returns the last child node as an element node, a text node or a comment node (depending on which one's last), while lastElementChild returns the last child node as an element node (ignores text and comment nodes).

##### createElement
The createElement() method creates an Element Node with the specified name.
Tip: After the element is created, use the element.appendChild() or element.insertBefore() method to insert it to the document.

```javascript
	// Create a div
var newDiv =  document.createElement('div');

// Add class
newDiv.className= 'hello';

// Add id
newDiv.id = 'hello1';

// Add attr
newDiv.setAttribute('title', 'Hello Div');

// Create text node
var newDivText = document.createTextNode('Hello World');

// Add text to div
newDiv.appendChild(newDivText);

var container = document.querySelector('header .container');
var h1 = document.querySelector('header h1');

console.log(newDiv);

newDiv.style.fontSize = '30px';

container.insertBefore(newDiv, h1);
```

##### insertBefore
The insertBefore() method inserts a node as a child, right before an existing child, which you specify.
Tip: If you want to create a new list item, with text, remember to create the text as a Text node which you append to the <li> element, then insert <li> to the list.


##### textContent/innerText/innerHTML
The textContent property sets or returns the text content of the specified node, and all its descendants.
If you set the textContent property, any child nodes are removed and replaced by a single Text node containing the specified string.
Note: This property is similar to the innerText property, however there are some differences:
textContent returns the text content of all elements, while innerText returns the content of all elements, except for <script> and <style> elements.
innerText will not return the text of elements that are hidden with CSS (textContent will).
Tip: Sometimes this property can be used instead of the nodeValue property, but remember that this property returns the text of all child nodes as well.
Tip: To set or return the HTML content of an element, use the innerHTML property.

ex:
The innerText property returns just the text, without spacing and inner element tags.
The innerHTML property returns the text, including all spacing and inner element tags.
The textContent property returns the text with spacing, but without inner element tags.


```javascript
// EXAMINE THE DOCUMENT OBJECT //

// console.dir(document);
// console.log(document.domain);
// console.log(document.URL);
// console.log(document.title);
// //document.title =  123;
// console.log(document.doctype);
// console.log(document.head);
// console.log(document.body);
// console.log(document.all);
// console.log(document.all[10]);
// // document.all[10].textContent = 'Hello';
// console.log(document.forms[0]);
// console.log(document.links);
// console.log(document.images);

// GETELEMENTBYID //
// console.log(document.getElementById('header-title'));
// var headerTitle = document.getElementById('header-title');
// var header = document.getElementById('main-header');
// console.log(headerTitle);
// headerTitle.textContent = 'Hello';
// headerTitle.innerText = 'Goodbye';
// console.log(headerTitle.innerText);
// headerTitle.innerHTML = '<h3>Hello</h3>';
// header.style.borderBottom = 'solid 3px #000';

// GETELEMENTSBYCLASSNAME //
// var items = document.getElementsByClassName('list-group-item');
// console.log(items);
// console.log(items[1]);
// items[1].textContent = 'Hello 2';
// items[1].style.fontWeight = 'bold';
// items[1].style.backgroundColor = 'yellow';

// // Gives error
// //items.style.backgroundColor = '#f4f4f4';

// for(var i = 0; i < items.length; i++){
//   items[i].style.backgroundColor = '#f4f4f4';
// }

// GETELEMENTSBYTAGNAME //
// var li = document.getElementsByTagName('li');
// console.log(li);
// console.log(li[1]);
// li[1].textContent = 'Hello 2';
// li[1].style.fontWeight = 'bold';
// li[1].style.backgroundColor = 'yellow';

// // Gives error
// //items.style.backgroundColor = '#f4f4f4';

// for(var i = 0; i < li.length; i++){
//   li[i].style.backgroundColor = '#f4f4f4';
// }

// QUERYSELECTOR //
// var header = document.querySelector('#main-header');
// header.style.borderBottom = 'solid 4px #ccc';

// var input = document.querySelector('input');
// input.value = 'Hello World'

// var submit = document.querySelector('input[type="submit"]');
// submit.value="SEND"

// var item = document.querySelector('.list-group-item');
// item.style.color = 'red';

// var lastItem = document.querySelector('.list-group-item:last-child');
// lastItem.style.color = 'blue';

// var secondItem = document.querySelector('.list-group-item:nth-child(2)');
// secondItem.style.color = 'coral';

// QUERYSELECTORALL //
// var titles = document.querySelectorAll('.title');

// console.log(titles);
// titles[0].textContent = 'Hello';

// var odd = document.querySelectorAll('li:nth-child(odd)');
// var even= document.querySelectorAll('li:nth-child(even)');

// for(var i = 0; i < odd.length; i++){
//   odd[i].style.backgroundColor = '#f4f4f4';
//   even[i].style.backgroundColor = '#ccc';
// }



// TRAVERSING THE DOM //
// var itemList = document.querySelector('#items');
// parentNode
// console.log(itemList.parentNode);
// itemList.parentNode.style.backgroundColor = '#f4f4f4';
// console.log(itemList.parentNode.parentNode.parentNode);

// parentElement
// console.log(itemList.parentElement);
// itemList.parentElement.style.backgroundColor = '#f4f4f4';
// console.log(itemList.parentElement.parentElement.parentElement);

// childNodes
// console.log(itemList.childNodes);

// console.log(itemList.children);
// console.log(itemList.children[1]);
// itemList.children[1].style.backgroundColor = 'yellow';

// // FirstChild
// console.log(itemList.firstChild);
// // firstElementChild
// console.log(itemList.firstElementChild);
// itemList.firstElementChild.textContent = 'Hello 1';


// lastChild
// console.log(itemList.lastChild);
// lastElementChild
// console.log(itemList.lastElementChild);
// itemList.lastElementChild.textContent = 'Hello 4';

// nextSibling
// console.log(itemList.nextSibling);
// // nextElementSibling
// console.log(itemList.nextElementSibling);

// previousSibling
// console.log(itemList.previousSibling);
// previousElementSibling
// console.log(itemList.previousElementSibling);itemList.previousElementSibling.style.color = 'green';

// createElement

// // Create a div
// var newDiv =  document.createElement('div');

// // Add class
// newDiv.className= 'hello';

// // Add id
// newDiv.id = 'hello1';

// // Add attr
// newDiv.setAttribute('title', 'Hello Div');

// // Create text node
// var newDivText = document.createTextNode('Hello World');

// // Add text to div
// newDiv.appendChild(newDivText);

// var container = document.querySelector('header .container');
// var h1 = document.querySelector('header h1');

// console.log(newDiv);

// newDiv.style.fontSize = '30px';

// container.insertBefore(newDiv, h1);

// EVENTS //

// var button = document.getElementById('button').addEventListener('click', buttonClick);

// function buttonClick(e){
//   //console.log('Button clicked');
//   // document.getElementById('header-title').textContent = 'Changed';
//   // document.querySelector('#main').style.backgroundColor = '#f4f4f4';
//   //console.log(e);

//   // console.log(e.target);
//   // console.log(e.target.id);
//   // console.log(e.target.className);
//   // console.log(e.target.classList);
//   // var output = document.getElementById('output');
//   // output.innerHTML = '<h3>'+e.target.id+'</h3>';

//   // console.log(e.type);

//   //console.log(e.clientX);
//   //console.log(e.clientY);

//   //console.log(e.offsetX);
//   //console.log(e.offsetY);

//   // console.log(e.altKey);
//   // console.log(e.ctrlKey);
//   // console.log(e.shiftKey);
// }

// var button = document.getElementById('button');
// var box = document.getElementById('box');

//button.addEventListener('click', runEvent);
//button.addEventListener('dblclick', runEvent);
//button.addEventListener('mousedown', runEvent);
//button.addEventListener('mouseup', runEvent);

//box.addEventListener('mouseenter', runEvent);
//box.addEventListener('mouseleave', runEvent);

//box.addEventListener('mouseover', runEvent);
//box.addEventListener('mouseout', runEvent);

// box.addEventListener('mousemove', runEvent);

// var itemInput = document.querySelector('input[type="text"]');
// var form = document.querySelector('form');
// var select = document.querySelector('select');

// itemInput.addEventListener('keydown', runEvent);
// itemInput.addEventListener('keyup', runEvent);
// itemInput.addEventListener('keypress', runEvent);

// itemInput.addEventListener('focus', runEvent);
// itemInput.addEventListener('blur', runEvent);

// itemInput.addEventListener('cut', runEvent);
// itemInput.addEventListener('paste', runEvent);

// itemInput.addEventListener('input', runEvent);

// select.addEventListener('change', runEvent);
// select.addEventListener('input', runEvent);

// form.addEventListener('submit', runEvent);

// function runEvent(e){
//   e.preventDefault();
//   console.log('EVENT TYPE: '+e.type);

  //console.log(e.target.value);
  // document.getElementById('output').innerHTML = '<h3>'+e.target.value+'</h3>';

  // output.innerHTML = '<h3>MouseX: '+e.offsetX+' </h3><h3>MouseY: '+e.offsetY+'</h3>';

  // document.body.style.backgroundColor = "rgb("+e.offsetX+","+e.offsetY+", 40)";
// }
```
