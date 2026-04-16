This project is for the tutorial for intro to backend

## Basic Workflow - Mongoose Schema

file name- user.model.js

1. **Import Mongoose**

```js
import mongoose, { Schema } from "mongoose";
```

2. **Define a Schema**  
   Specify the structure and validation rules

```js
const userSchema = new Schema({
  username: { type: String, required: true },
  email: { type: String, required: true },
});
```

3. **Create a Model**  
   Creates a collection in MongoDB and lets you query/manipulate data

```js
export const User = mongoose.model("user", userSchema);
```

4. **Use the model**  
   In your controller files, import and use it to create/read/update/delete users

```js
import { User } from "../models/user.model.js";

// Create
const newUser = await User.create({
  username: "john",
  email: "john@example.com",
});

// Read
const user = await User.findById(id);

// Update
await User.updateOne({ _id: id }, { username: "newname" });

// Delete
await User.deleteOne({ _id: id });
```

So, once your model is set up, you use standared Mongoose methods in your controller logic to interact with the database.
