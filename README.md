# Designing-and-Implementing-a-Circular-Queue-In-JAVASCRIPT
This is a detailed explanation of designing and implementing a circular queue in javascript without using any inbuilt datastructures 

Circular Queue Implementation in JavaScript
Introduction
This repository contains a JavaScript implementation of a circular queue, solving the problem of designing a circular queue based on the FIFO principle. The circular queue, also known as a "Ring Buffer," is a linear data structure where the last position is connected back to the first position, creating a circular structure.

Question  -------------------------->

L E E T C O D E 
622. Design Circular Queue
Medium
3.4K
264
Companies
Design your implementation of the circular queue. The circular queue is a linear data structure in which the operations are performed based on FIFO (First In First Out) principle, and the last position is connected back to the first position to make a circle. It is also called "Ring Buffer".

One of the benefits of the circular queue is that we can make use of the spaces in front of the queue. In a normal queue, once the queue becomes full, we cannot insert the next element even if there is a space in front of the queue. But using the circular queue, we can use the space to store new values.

Implement the MyCircularQueue class:

MyCircularQueue(k) Initializes the object with the size of the queue to be k.
int Front() Gets the front item from the queue. If the queue is empty, return -1.
int Rear() Gets the last item from the queue. If the queue is empty, return -1.
boolean enQueue(int value) Inserts an element into the circular queue. Return true if the operation is successful.
boolean deQueue() Deletes an element from the circular queue. Return true if the operation is successful.
boolean isEmpty() Checks whether the circular queue is empty or not.
boolean isFull() Checks whether the circular queue is full or not.
You must solve the problem without using the built-in queue data structure in your programming language. 


SOLUTION -------------------------->
/**
 * @param {number} k
 */
var MyCircularQueue = function (k) {
    this.queue = []; // Initializing a queue
    this.size = k; // with the provided size.
};

/** 
 * @param {number} value
 * @return {boolean}
 */
MyCircularQueue.prototype.enQueue = function (value) {
    // Enqueue means adding the element in the queue.
    if (this.size === this.queue.length) return false; // its the case when queue is full, implies we cant add more elements in it.
    this.queue.push(value); // if not full then add the element 
    return true; // and return true as the operation is performed.
};

/**
 * @return {boolean}
 */
MyCircularQueue.prototype.deQueue = function () {
    if (this.queue.length === 0) return false; // its the case when queue is empty, implies we cant take out any more elements in it.
    this.queue.shift(); // if not empty then take out element from front.
    return true; // and return true as the operation is performed.
};

/**
 * @return {number}
 */
MyCircularQueue.prototype.Front = function () {
    if (this.queue.length) return this.queue[0]; // if we have something in queue then return the front element.
    else return -1; // if we dont have anything in the queue.

};

/**
 * @return {number}
 */
MyCircularQueue.prototype.Rear = function () {
    if (this.queue.length) return this.queue[this.queue.length - 1]; // if we have something in queue then return the last element.
    else return -1;  // if we dont have anything in the queue.
};

/**
 * @return {boolean}
 */
MyCircularQueue.prototype.isEmpty = function () {
    //returns true if found empty
    return this.queue.length === 0; // its the case when we dont have anything in the queue. 
};

/**
 * @return {boolean}
 */
MyCircularQueue.prototype.isFull = function () {
    //returns true if found full
    return this.queue.length === this.size; // its the case when the queue is full.
};

/** 
 * Your MyCircularQueue object will be instantiated and called as such:
 * var obj = new MyCircularQueue(k)
 * var param_1 = obj.enQueue(value)
 * var param_2 = obj.deQueue()
 * var param_3 = obj.Front()
 * var param_4 = obj.Rear()
 * var param_5 = obj.isEmpty()
 * var param_6 = obj.isFull()
 */
