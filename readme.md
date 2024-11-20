Here’s a detailed yet beginner-friendly **README.md** file for your random profile generator project:

---

# **Random Profile Generator**

## **Project Overview**

The **Random Profile Generator** is a web application that fetches random user data from the [Random User API](https://randomuser.me/) and dynamically displays the user's profile on the page. This project uses **vanilla JavaScript** and demonstrates key concepts like working with APIs, DOM manipulation, event handling, and conditional styling.

---

## **Features**

1. **Fetch Random User Profiles**:
   - Retrieves user data such as name, email, phone number, and age from the Random User API.

2. **Dynamic Content Rendering**:
   - Displays the fetched user profile dynamically on the web page without reloading.

3. **Gender-Based Background Color**:
   - Changes the background color based on the user’s gender:
     - **Purple** for female.
     - **Steel blue** for male.

4. **Loading Spinner**:
   - Shows a spinner while the user profile is being fetched to enhance the user experience.

5. **Button to Generate New Profiles**:
   - A "Generate" button fetches a new random user profile every time it’s clicked.

---

## **How It Works**

### **1. Fetching User Data**
- The app makes a `GET` request to the Random User API using the **`fetch()`** method.
- After receiving the response, it parses the data and passes the user details to the `displayUser` function.

**Code Example**:
```javascript
fetch('https://randomuser.me/api')
  .then((response) => response.json())
  .then((data) => {
    displayUser(data.results[0]);
  });
```

---

### **2. Displaying User Profiles**
- The `displayUser` function dynamically updates the HTML structure with the fetched user data using template literals.

**Dynamic Structure**:
```javascript
userDisplay.innerHTML = `
  <p><span class="font-bold">Name: </span> ${user.name.first} ${user.name.last}</p>
  <p><span class="font-bold">Email: </span> ${user.email}</p>
  <p><span class="font-bold">Phone: </span> ${user.phone}</p>
  <p><span class="font-bold">Age: </span> ${user.dob.age}</p>
`;
```

---

### **3. Gender-Based Background Color**
- The app changes the background color based on the gender of the user. This provides visual differentiation between male and female users.

**Code Example**:
```javascript
if (user.gender === 'female') {
  document.body.style.backgroundColor = 'rebeccapurple';
} else {
  document.body.style.backgroundColor = 'steelblue';
}
```

---

### **4. Spinner Functionality**
- A spinner appears while the data is being fetched and disappears once the data is displayed.
- This is controlled by the `showSpinner` and `hideSpinner` functions.

**Code Example**:
```javascript
const showSpinner = () => {
  document.querySelector('.spinner').style.display = 'block';
};

const hideSpinner = () => {
  document.querySelector('.spinner').style.display = 'none';
};
```

---

## **Why I Built This**

1. **To Learn API Integration**:
   - Practiced making asynchronous requests and handling responses.

2. **To Improve DOM Manipulation Skills**:
   - Enhanced understanding of dynamically updating the DOM with JavaScript.

3. **To Experiment with Conditional Styling**:
   - Learned how to apply different styles programmatically based on fetched data.

4. **To Understand User Interaction**:
   - Built event listeners for user-triggered actions like clicking the "Generate" button.

---

## **Lessons Learned**

- **Asynchronous Programming**:
  - Using `fetch()` for API requests and handling promises with `.then()` for chaining responses.
  
- **Template Literals**:
  - Efficiently injecting dynamic data into HTML structure.

- **Separation of Concerns**:
  - Keeping responsibilities clear by creating reusable functions like `showSpinner` and `hideSpinner`.

---

## **How to Run**

1. Clone the repository:
   ```bash
   git clone https://github.com/BenjaminChukwu05/Random_Profile_Generator.git
   ```
2. Open the `index.html` file in a web browser.

3. Click the "Generate" button to fetch and display a random user profile.

---

## **Future Improvements**

- Add error handling for failed API requests.
- Display more user details such as nationality or time zone.
- Include a feature to save favorite profiles locally.