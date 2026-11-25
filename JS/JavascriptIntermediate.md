All code snippets explained in **Part 2 – Master JavaScript & Become a Real Developer | Full Course** by Sheryians Coding School, organized by section with timestamps.
 
 [![Part 2 – Master JavaScript & Become a Real Developer | Full Course](https://i.ytimg.com/vi/1aR7tcmWo_w/maxresdefault.jpg)](http://www.youtube.com/watch?v=1aR7tcmWo_w)

> Click the thumbnail to open the full video. Every timestamp below jumps to that exact moment on YouTube.

---

## 1. DOM Manipulation

### Selecting Elements `[00:13:05]`

```js
// By ID (no '#' prefix)
let byId = document.getElementById("abcd");
console.dir(byId); // Opens inspectable DOM node object

// By Class Name (returns HTMLCollection) [00:14:57]
let byClass = document.getElementsByClassName("abcd");

// Modern selectors (CSS syntax) [00:16:35]
let firstH1 = document.querySelector("h1");      // First matching element
let allH1s = document.querySelectorAll("h1");    // NodeList of all matches

```

### Text, HTML & Property Manipulation `[00:21:28]`

```js
let h1 = document.querySelector("h1");

// Text vs HTML
h1.textContent = "Hello Harsh kaise ho"; // Faster, includes hidden text
h1.innerText = "Harsh badhiya hai";      // Visible text only
h1.innerHTML = "<i>hey</i>";             // Parses HTML tags [00:24:31]

// Direct DOM property manipulation [00:25:37]
h1.hidden = true;

```

### Attribute Manipulation `[00:29:11]`

```js
let a = document.querySelector("a");
a.href = "https://www.google.com";
a.setAttribute("href", "https://www.google.com");
console.log(a.getAttribute("href"));     // Reads attribute value [00:36:45]
a.removeAttribute("href");               // Removes attribute [00:38:01]

// Setting image src dynamically [00:34:30]
let img = document.querySelector("img");
img.setAttribute("src", "https://images.unsplash.com/...");

```

### Dynamic DOM Creation & Removal `[00:42:14]`

```js
let h1 = document.createElement("h1");
h1.textContent = "Hello ji kaise ho";

document.body.appendChild(h1);  // Adds at the end of body
document.body.prepend(h1);      // Adds at the start of body
h1.remove();                    // Removes element directly [00:46:29]

// Appending inside a specific container [00:47:33]
let div = document.querySelector("div");
div.append(h1);
div.prepend(h1);

```

### CSS Styles & `classList` `[00:52:17]`

```js
let h1 = document.querySelector("h1");

// Inline styles (camelCase properties)
h1.style.color = "red";
h1.style.backgroundColor = "yellow";
h1.style.fontFamily = "Gilroy";
h1.style.textTransform = "capitalize";

// Preferred approach: toggling CSS classes [00:57:16]
h1.classList.add("hulu");
h1.classList.remove("hulu");
h1.classList.toggle("hulu"); // Adds if missing, removes if present

```

### DOM Practice Tasks `[01:06:31]`

```js
// Select all buttons with class .buy-now
let buyNowBtns = document.querySelectorAll(".buy-now");

// Select heading by ID and update text [01:07:56]
let heading = document.querySelector("#heading");
heading.textContent = "Welcome to Sheryians";

// Print text of all <li> items (forEach and for loop) [01:09:03]
let lis = document.querySelectorAll("li");
lis.forEach(function (val) {
  console.log(val.textContent);
});

for (let i = 0; i < lis.length; i++) {
  console.log(lis[i].textContent);
}

// Replace paragraph HTML [01:15:15]
let p = document.querySelector("p");
p.innerHTML = "<b>Updated</b> by JavaScript";

// Add title attribute to a div & enable a disabled button [01:21:27]
let div = document.querySelector("div");
div.setAttribute("title", "some info");

let btn = document.querySelector("button");
btn.removeAttribute("disabled");

// Append new <li> to <ul> [01:25:40]
let ul = document.querySelector("ul");
let li = document.createElement("li");
li.textContent = "New Task";
ul.appendChild(li);

// Prepend placeholder image inside a div [01:27:01]
let newImg = document.createElement("img");
newImg.setAttribute("src", "https://example.com/placeholder.jpg");
newImg.classList.add("placeholder");
document.querySelector("div").prepend(newImg);

// Remove first <li> from <ul> using removeChild [01:30:12]
let firstLi = document.querySelector("li");
ul.removeChild(firstLi);

// Highlight every even <li> [01:32:13]
let evenLis = document.querySelectorAll("ul li:nth-child(2n)");
evenLis.forEach(function (elem) {
  elem.classList.add("highlight");
});

// Set fontSize to 18px on all <p> elements [01:35:25]
document.querySelectorAll("p").forEach(function (elem) {
  elem.style.fontSize = "18px";
});

```

---

## 2. Events & Event Handling

### Adding & Removing Event Listeners `[01:44:19]`

```js
let h1 = document.querySelector("h1");
h1.addEventListener("click", function () {
  h1.style.color = "red";
});

// Removing a listener requires the exact same function reference [01:51:09]
let p = document.querySelector("p");
function dblclick() {
  p.style.color = "yellow";
}
p.addEventListener("dblclick", dblclick);
p.removeEventListener("dblclick", dblclick);

```

### `input` & `change` Events `[02:02:29]`

```js
// Log each typed character (ignoring backspace where data is null)
let inp = document.querySelector("input");
inp.addEventListener("input", function (dets) {
  if (dets.data !== null) {
    console.log(dets.data);
  }
});

// Dropdown <select> change listener [02:15:28]
let sel = document.querySelector("select");
let device = document.querySelector("#device");

sel.addEventListener("change", function (dets) {
  device.textContent = `${dets.target.value} Device Selected`;
});

```

### Keypress Screen Display (`keydown`) `[02:27:08]`

```js
let h1 = document.querySelector("h1");

window.addEventListener("keydown", function (dets) {
  if (dets.key === " ") {
    h1.textContent = "SPC";
  } else {
    h1.textContent = dets.key;
  }
});

```

### Custom File Upload Button `[02:35:50]`

```js
let btn = document.querySelector("#btn");
let fileinp = document.querySelector("#fileinp");

// Clicking custom styled div triggers hidden <input type="file">
btn.addEventListener("click", function () {
  fileinp.click();
});

// Display chosen file name safely (handles Cancel click) [02:43:21]
fileinp.addEventListener("change", function (dets) {
  const file = dets.target.files[0];
  if (file) {
    btn.textContent = file.name;
  }
});

```

### Dynamic Profile Card Generator on Form Submit `[02:51:08]`

```js
let form = document.querySelector("form");
let inputs = document.querySelectorAll("input");
let main = document.querySelector("#main");

form.addEventListener("submit", function (dets) {
  dets.preventDefault(); // Stops page reload

  let card = document.createElement("div");
  card.classList.add("card");

  let profile = document.createElement("div");
  profile.classList.add("profile");

  let img = document.createElement("img");
  img.setAttribute("src", inputs[0].value);

  let h3 = document.createElement("h3");
  h3.textContent = inputs[1].value;

  let h5 = document.createElement("h5");
  h5.textContent = inputs[2].value;

  let p = document.createElement("p");
  p.textContent = inputs[3].value;

  profile.appendChild(img);
  card.appendChild(profile);
  card.appendChild(h3);
  card.appendChild(h5);
  card.appendChild(p);
  main.appendChild(card);

  // Clear all inputs except the submit button [03:13:56]
  inputs.forEach(function (inp) {
    if (inp.type !== "submit") {
      inp.value = "";
    }
  });
});

```

### Mouse Events (`mouseover`, `mouseout`, `mousemove`) `[03:21:33]`

```js
let abcd = document.querySelector("#abcd");

// Hover color change
abcd.addEventListener("mouseover", function () {
  abcd.style.backgroundColor = "yellow";
});
abcd.addEventListener("mouseout", function () {
  abcd.style.backgroundColor = "red";
});

// Cursor-following element (requires position: absolute on #abcd) [03:25:46]
window.addEventListener("mousemove", function (dets) {
  abcd.style.top = dets.clientY + "px";
  abcd.style.left = dets.clientX + "px";
});

```

### Event Bubbling, Delegation & Capturing `[03:45:42]`

```js
// Event Delegation: single listener on <ul> toggles strikethrough class on clicked <li>
let ul = document.querySelector("ul");
ul.addEventListener("click", function (dets) {
  dets.target.classList.toggle("lt");
});

// Event Capturing (3rd argument = true) vs Bubbling (default false) [04:01:29]
let a = document.querySelector(".a");
let b = document.querySelector(".b");
let c = document.querySelector(".c");
let btn = document.querySelector("button");

// Capturing runs top-down first (a -> c), then bubbling runs bottom-up (btn -> b)
btn.addEventListener("click", function () {
  console.log("button clicked");
});
c.addEventListener("click", function () {
  console.log("c clicked");
}, true);
b.addEventListener("click", function () {
  console.log("b clicked");
});
a.addEventListener("click", function () {
  console.log("a clicked");
}, true);

```

### Live Character Counter `[04:07:40]`

```js
let inp = document.querySelector("input");
let span = document.querySelector("span");

inp.addEventListener("input", function () {
  let left = 20 - inp.value.length;
  span.textContent = left;

  if (left < 0) {
    span.style.color = "red";
  } else {
    span.style.color = "white";
  }
});

```

---

## 3. Forms & Form Validation

### Basic Validation & HTML Inline Attributes `[04:22:32]`

```html
<!-- Inline HTML validation attributes [04:31:44] -->
<input type="text" required minlength="3" maxlength="10" pattern="[a-z]{3,8}" />

```

```js
let nm = document.querySelector("#name");
let form = document.querySelector("form");

form.addEventListener("submit", function (dets) {
  dets.preventDefault();

  if (nm.value.length <= 2) {
    document.querySelector("#hide").style.display = "initial";
  } else {
    document.querySelector("#hide").style.display = "none";
  }
});

```

### Regex Testing & Email/Password Validator `[04:42:07]`

```js
let email = document.querySelector("#email");
let password = document.querySelector("#password");
let form = document.querySelector("form");

form.addEventListener("submit", function (dets) {
  dets.preventDefault();

  // Reset previous error messages
  document.querySelector("#emailError").textContent = "";
  document.querySelector("#passwordError").textContent = "";

  const emailRegex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
  const passwordRegex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/;

  let emailans = emailRegex.test(email.value);
  let passwordans = passwordRegex.test(password.value);
  let isValid = true;

  if (!emailans) {
    document.querySelector("#emailError").textContent = "Email is incorrect";
    document.querySelector("#emailError").style.display = "initial";
    isValid = false;
  }

  if (!passwordans) {
    document.querySelector("#passwordError").textContent = "Password is incorrect";
    document.querySelector("#passwordError").style.display = "initial";
    isValid = false;
  }

  if (isValid) {
    document.querySelector("#resultMessage").textContent = "Everything is correct";
  }
});

```

---

## 4. Timers & Intervals

### `setTimeout`, `setInterval`, `clearTimeout`, `clearInterval` & Countdown `[05:00:16]`

```js
// Run once after 3 seconds, then cancel it [05:02:17]
let tm = setTimeout(function () {
  console.log("hey");
}, 3000);
clearTimeout(tm);

// Countdown from 10 to 0 [05:06:37]
let count = 10;
let interval = setInterval(function () {
  if (count >= 0) {
    console.log(count);
    count--;
  } else {
    clearInterval(interval);
  }
}, 1000);

```

### Download Progress Bar Simulator `[05:09:25]`

```js
let count = 0;
let seconds = 5;
let progress = document.querySelector(".progress-bar");
let percentText = document.querySelector("#percentText");

let intv = setInterval(function () {
  if (count <= 99) {
    count++;
    progress.style.width = `${count}%`;
    percentText.textContent = `${count}%`;
  } else {
    document.querySelector("h2").textContent = "Downloaded.";
    clearInterval(intv);
  }
}, (seconds * 1000) / 100);

```

---

## 5. `localStorage`, `sessionStorage` & Cookies

### Storage APIs & JSON Serialization `[05:23:32]`

```js
// localStorage (persists across browser restarts)
localStorage.setItem("name", "harsh");
let val = localStorage.getItem("name");
localStorage.setItem("name", "harshita"); // Overwrites existing key
localStorage.removeItem("name");
localStorage.clear();

// sessionStorage (clears when tab closes) [05:28:09]
sessionStorage.setItem("name", "harsh");
sessionStorage.clear();

// Cookies (~4KB, sent to server on reload) [05:33:54]
document.cookie = "email=harsh@test.com";
document.cookie = "age=26";

// Storing & retrieving Arrays/Objects in localStorage [05:39:16]
localStorage.setItem("friends", JSON.stringify(["akash", "harsh", "amit"]));
let fr = JSON.parse(localStorage.getItem("friends"));
console.log(fr);

```

### Theme Preference (OS Sync + Toggle + Persistence) `[05:44:21]`

```js
function applyTheme(theme) {
  document.body.classList.remove("dark", "light");
  document.body.classList.add(theme);
}

function getSystemTheme() {
  return window.matchMedia("(prefers-color-scheme: dark)").matches
    ? "dark"
    : "light";
}

function setInitialTheme() {
  const savedTheme = localStorage.getItem("theme");
  applyTheme(savedTheme || getSystemTheme());
}

setInitialTheme();

// Live OS theme change listener (only overrides if user hasn't manually saved a theme)
window
  .matchMedia("(prefers-color-scheme: dark)")
  .addEventListener("change", function () {
    if (!localStorage.getItem("theme")) {
      applyTheme(getSystemTheme());
    }
  });

// Manual toggle button
let btn = document.querySelector("button");
btn.addEventListener("click", function () {
  const current = document.body.classList.contains("dark") ? "dark" : "light";
  const next = current === "dark" ? "light" : "dark";
  applyTheme(next);
  localStorage.setItem("theme", next);
});

```

---

## 6. Final Projects

### Project 1: Real-Time User Search Filter `[06:05:35]`

```js
let users = [
  {
    name: "amisha rathore",
    pic: "https://example.com/pic1.jpg",
    bio: "silent chaos in a loud world",
  },
  {
    name: "amita mehta",
    pic: "https://example.com/pic2.jpg",
    bio: "main character energy",
  },
  {
    name: "isha oberoi",
    pic: "https://example.com/pic3.jpg",
    bio: "walking through dreams in doc martens",
  },
];

function showUsers(arr) {
  arr.forEach(function (user) {
    const card = document.createElement("div");
    card.classList.add("card");

    const img = document.createElement("img");
    img.src = user.pic;
    img.classList.add("bg-img");

    const blurredLayer = document.createElement("div");
    blurredLayer.style.backgroundImage = `url(${user.pic})`;
    blurredLayer.classList.add("blurred-layer");

    const content = document.createElement("div");
    content.classList.add("content");

    const heading = document.createElement("h3");
    heading.textContent = user.name;

    const para = document.createElement("p");
    para.textContent = user.bio;

    content.appendChild(heading);
    content.appendChild(para);
    card.appendChild(img);
    card.appendChild(blurredLayer);
    card.appendChild(content);

    document.querySelector(".cards").appendChild(card);
  });
}

showUsers(users);

// Filter users on every input keystroke [06:14:01]
let inp = document.querySelector(".inp");
inp.addEventListener("input", function () {
  let newUsers = users.filter((user) => {
    return user.name.startsWith(inp.value);
  });

  document.querySelector(".cards").innerHTML = "";
  showUsers(newUsers);
});

```

### Project 2: Call Reminder / Stacked Notes App `[06:30:34]`

```js
// DOM Selections
let addNote = document.querySelector("#add-note");
let formContainer = document.querySelector(".form-container");
let closeForm = document.querySelector(".closeForm");
const form = document.querySelector("form");

const imageUrlInput = form.querySelector('input[placeholder="https://example.com/photo.jpg"]');
const fullNameInput = form.querySelector('input[placeholder="Enter full name"]');
const homeTownInput = form.querySelector('input[placeholder="Enter home town"]');
const purposeInput = form.querySelector('input[placeholder="e.g., Quick appointment note"]');
const categoryRadios = form.querySelectorAll('input[name="category"]');

const stack = document.querySelector(".stack");
const upBtn = document.querySelector("#upBtn");
const downBtn = document.querySelector("#downBtn");

// LocalStorage persistence helper [06:47:47]
function saveToLocalStorage(obj) {
  if (localStorage.getItem("tasks") === null) {
    let oldTasks = [];
    oldTasks.push(obj);
    localStorage.setItem("tasks", JSON.stringify(oldTasks));
  } else {
    let oldTasks = JSON.parse(localStorage.getItem("tasks"));
    oldTasks.push(obj);
    localStorage.setItem("tasks", JSON.stringify(oldTasks));
  }
}

// Toggle Form Modal
addNote.addEventListener("click", function () {
  formContainer.style.display = "initial";
});

closeForm.addEventListener("click", function () {
  formContainer.style.display = "none";
});

// Form Validation & Submission [06:36:42]
form.addEventListener("submit", function (evt) {
  evt.preventDefault();

  const imageUrl = imageUrlInput.value.trim();
  const fullName = fullNameInput.value.trim();
  const homeTown = homeTownInput.value.trim();
  const purpose = purposeInput.value.trim();

  let selected = false;
  categoryRadios.forEach(function (cat) {
    if (cat.checked) {
      selected = cat.value;
    }
  });

  if (imageUrl === "") return alert("Please enter an Image URL.");
  if (fullName === "") return alert("Please enter your Full Name.");
  if (homeTown === "") return alert("Please enter your Home Town.");
  if (purpose === "") return alert("Please enter the Purpose.");
  if (!selected) return alert("Please select a category");

  saveToLocalStorage({ imageUrl, fullName, homeTown, purpose, selected });

  form.reset();
  formContainer.style.display = "none";
  showCards();
});

// Render cards from localStorage [07:00:05]
function showCards() {
  stack.innerHTML = "";
  let allTasks = JSON.parse(localStorage.getItem("tasks")) || [];

  allTasks.forEach(function (task) {
    const card = document.createElement("div");
    card.classList.add("card");

    const avatar = document.createElement("img");
    avatar.src = task.imageUrl;
    avatar.alt = "profile";
    avatar.classList.add("avatar");
    card.appendChild(avatar);

    const name = document.createElement("h2");
    name.textContent = task.fullName;
    card.appendChild(name);

    const hometownInfo = document.createElement("div");
    hometownInfo.classList.add("info");
    const hometownLabel = document.createElement("span");
    hometownLabel.textContent = "Home town";
    const hometownValue = document.createElement("span");
    hometownValue.textContent = task.homeTown;
    hometownInfo.appendChild(hometownLabel);
    hometownInfo.appendChild(hometownValue);
    card.appendChild(hometownInfo);

    const bookingsInfo = document.createElement("div");
    bookingsInfo.classList.add("info");
    const bookingsLabel = document.createElement("span");
    bookingsLabel.textContent = "Purpose";
    const bookingsValue = document.createElement("span");
    bookingsValue.textContent = task.purpose;
    bookingsInfo.appendChild(bookingsLabel);
    bookingsInfo.appendChild(bookingsValue);
    card.appendChild(bookingsInfo);

    const buttonsDiv = document.createElement("div");
    buttonsDiv.classList.add("buttons");

    const callBtn = document.createElement("button");
    callBtn.classList.add("call");
    callBtn.innerHTML = '<i class="ri-phone-line"></i> Call';

    const msgBtn = document.createElement("button");
    msgBtn.classList.add("msg");
    msgBtn.textContent = "Message";

    buttonsDiv.appendChild(callBtn);
    buttonsDiv.appendChild(msgBtn);
    card.appendChild(buttonsDiv);

    stack.appendChild(card);
  });
}

showCards();

// Update 3D stack positions for top 3 visible cards [07:12:00]
function updateStack() {
  const cards = document.querySelectorAll(".stack .card");

  for (let i = 0; i < 3; i++) {
    if (!cards[i]) break;
    cards[i].style.zIndex = 3 - i;
    cards[i].style.transform = `translateY(${i * 10}px) scale(${1 - i * 0.02})`;
    cards[i].style.opacity = `${1 - i * 0.02}`;
  }
}

// Rotate stack up / down [07:09:29]
upBtn.addEventListener("click", function () {
  let lastChild = stack.lastElementChild;
  if (lastChild) {
    stack.insertBefore(lastChild, stack.firstElementChild);
    updateStack();
  }
});

downBtn.addEventListener("click", function () {
  const firstChild = stack.firstElementChild;
  if (firstChild) {
    stack.appendChild(firstChild);
    updateStack();
  }
});

```