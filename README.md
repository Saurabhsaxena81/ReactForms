# React Forms Learning

## Introduction

This repository documents my learning about handling forms in React.js. Forms are an essential part of web applications, allowing users to input and submit data. React provides a way to handle forms efficiently using controlled and uncontrolled components.

## Topics Covered

### 1. Controlled Components

- Form elements like input, textarea, and select are controlled by React state.
- Example:

```jsx
import React, { useState } from "react";

function ControlledForm() {
  const [name, setName] = useState("");

  const handleChange = (event) => {
    setName(event.target.value);
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    alert(`Submitted Name: ${name}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" value={name} onChange={handleChange} />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default ControlledForm;
```

### 2. Uncontrolled Components

- Uses `useRef()` to directly access the DOM element.
- Example:

```jsx
import React, { useRef } from "react";

function UncontrolledForm() {
  const inputRef = useRef(null);

  const handleSubmit = (event) => {
    event.preventDefault();
    alert(`Submitted Name: ${inputRef.current.value}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" ref={inputRef} />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default UncontrolledForm;
```

### 3. Handling Multiple Inputs

- Use a single state object to manage multiple input fields.
- Example:

```jsx
import React, { useState } from "react";

function MultiInputForm() {
  const [formData, setFormData] = useState({ name: "", email: "" });

  const handleChange = (event) => {
    const { name, value } = event.target;
    setFormData({ ...formData, [name]: value });
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    alert(`Name: ${formData.name}, Email: ${formData.email}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input
          type="text"
          name="name"
          value={formData.name}
          onChange={handleChange}
        />
      </label>
      <label>
        Email:
        <input
          type="email"
          name="email"
          value={formData.email}
          onChange={handleChange}
        />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default MultiInputForm;
```

### 4. Form Validation

- Basic form validation using state and conditions.
- Example:

```jsx
import React, { useState } from "react";

function FormValidation() {
  const [email, setEmail] = useState("");
  const [error, setError] = useState("");

  const handleChange = (event) => {
    setEmail(event.target.value);
    setError("");
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    if (!email.includes("@")) {
      setError("Invalid email address");
    } else {
      alert(`Submitted Email: ${email}`);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Email:
        <input type="email" value={email} onChange={handleChange} />
      </label>
      {error && <p style={{ color: "red" }}>{error}</p>}
      <button type="submit">Submit</button>
    </form>
  );
}

export default FormValidation;
```

## Conclusion

This learning repository explores different ways of handling forms in React. It covers controlled components, uncontrolled components, handling multiple inputs, and form validation.

## Future Enhancements

- Implement advanced form handling using Formik and Yup.
- Add real-time validation and error messages.
- Integrate form submissions with a backend API.

---

## Author

[Saurabh Saxena](https://github.com/Saurabhsaxena81)

## License

This project is open-source and available under the MIT License.
