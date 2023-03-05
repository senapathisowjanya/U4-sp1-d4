# U4-sp1-d4
Props:- Props are short for properties, which are passed to a component from its parent. Props are read-only, meaning they cannot be modified by the component that receives them. Props are used to pass data or configuration settings to child components, which allows for greater reusability of components.

State:-  State, on the other hand, is used to manage component-specific data that can change over time. State is defined within a component and can be updated by the component itself using the setState() method. Unlike props, state is mutable, which means it can be updated and modified by the component. State is used to manage the internal state of a component and to reflect changes in the UI as the user interacts with the component.

UseState API:- 
The useState API is a built-in React Hook that allows functional components to manage and update state. It is a simpler and more concise way of managing state than using traditional class-based components with a setState method.

Filter:-
filter() is used to iterate through an array and return a new array with only the elements that meet a certain condition. It takes a function as an argument, which is called for each element in the array. The function should return a boolean value, indicating whether the element should be included in the new array.

Map:-
map() is used to iterate through an array and return a new array with modified elements. It takes a function as an argument, which is called for each element in the array. The function can modify the element and return a new value, which is added to the new array.

Reduce:-
reduce() is used to iterate through an array and reduce it to a single value. It takes a function as an argument, which is called for each element in the array. The function should take two arguments: an accumulator and the current element. The accumulator is used to keep track of the accumulated value as the function is called for each element. The function should return the updated accumulator value.


import React, { useState } from "react";

function Todo() {
  const [tasks, setTasks] = useState([]);
  Array.prototype.myMap = function(callback) {
    const marray = [];
    for (let i = 0; i < this.length; i++) {
      marray.push(callback(this[i], i, this));
    }
    return marray;
  };

  Array.prototype.myFilter = function(callback) {
    const farray = [];
    for (let i = 0; i < this.length; i++) {
      if (callback(this[i], i, this)) {
        farray.push(this[i]);
      }
    }
    return farray;
  };

  Array.prototype.myReduce = function(callback, initialValue) {
    let acc = initialValue !== undefined ? initialValue : this[0];
    const item = initialValue !== undefined ? 0 : 1;
    for (let i = item; i < this.length; i++) {
      acc = callback(acc, this[i], i, this);
    }
    return acc;
  };

  const change = (event) => {
    setNewTask(event.target.value);
  };

  const AddTask = () => {
    if (newTask !== "") {
      setTasks([...tasks, { title: newTask, completed: false }]);
      setNewTask("");
    }
  };

   const TaskToggle = (index) => {
    const newTasks = [...tasks];
    newTasks[index].completed = !newTasks[index].completed;
    setTasks(newTasks);
  };

  return (
    <div className="todo-container">
      <h1>Todo List</h1>
      <div className="input-container">
        <input
          type="text"
          value={newTask}
          onChange={handleNewTaskChange}
        />
        <button onClick={AddTask}>Add</button>
      </div>
      <div className="task-list">
        {task
          .myMap((task, index) => (
            <div
              key={index}
              className={`task ${task.completed ? "completed" : ""}`}
              onClick={() => handleTaskToggle(index)
              {task.title}
            </div>
          ))}
      </div>
    </div>
  );
}

export default Todo;
