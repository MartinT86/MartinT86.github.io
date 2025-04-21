---
layout: post
title: "Linked list"
description: "An overview of the Linked List data structure"
tags: [Data Structures]
---

Honestly, I don't think I've ever used the linked list data structure in the wild before. But I came across it when I was doing some coding practice the other day. I found it super interesting to learn a data structure that isn't just the array that we often use.

So here is a blog post to cement the learning and create myself a reminder for the future.

## What is a linked list?

A linked list is a data structure made up from a sequence of nodes. Each node has two properties; the data itself, and the pointer to the next node in the sequence. The linked list itself will also have the reference to the starting node, or "head".

## Example code

Here is an example node; with it's "data" and "next" properties.
```typescript
class ListNode {
    data: string
    next: ListNode | null = null
    constructor(data: string) {
        this.data = data
    }
}
```

Below are some example functions for a linked list.

Add:
Adding a node to the end of the list
```typescript
add(node: ListNode) {
    if (!this.head) {
        this.head = node
    } else {
        let nextNode = this.head
        while (nextNode?.next) {
            nextNode = nextNode.next
        }
        if (nextNode) {
            nextNode.next = node
        }
    }
}
```

Insert:
Inserting a node at the start of the list
```typescript
insert(node: ListNode) {
    if (!this.head) {
        this.head = node
    } else {
        const prevHead = this.head
        this.head = node
        this.head.next = prevHead
    }
}
```

Shift:
Removing and returning the node at the start of the list
```typescript
shift(): ListNode {
    if (!this.head) {
        throw new Error("Empty list");
    }
    if (!this.head.next) {
        const prevHead = this.head
        this.head = null
        return prevHead
    }
    const prevHead = this.head
    this.head = prevHead.next
    return prevHead
}
```

Pop:
Removing and returning the node at the end of the list
```typescript
pop(): ListNode {
    if (!this.head) {
        throw new Error("Empty list");
    }
    if (!this.head.next) {
        const prevHead = this.head
        this.head = null
        return prevHead
    }
    let prevNode = this.head
    let currentNode = this.head
    while (currentNode.next) {
        prevNode = currentNode
        currentNode = currentNode.next
    }
    prevNode.next = null
    return currentNode
}
```

Delete:
Removing the first node that matches a given data value
```typescript
delete(data: string) {
    if (!this.head) {
        throw new Error("Empty list");
    }
    if (this.head.next == null && this.head.data == data) {
        this.head = null
    } else {
        let prevNode = this.head
        let currentNode = this.head
        while (currentNode.next) {
            prevNode = currentNode
            currentNode = currentNode.next
            if (currentNode.data == data) {
                prevNode.next = currentNode.next
            }
        }
    }
}
```

Count:
Return the count of the nodes in a list
```typescript
get count():number {
    if (!this.head) {
        return 0
    }
    let nodeCount = 1
    let currentNode = this.head
    while(currentNode?.next) {
        currentNode = currentNode.next
        nodeCount++
    }
    return nodeCount
}
```

The full example code can be found [here.](https://github.com/MartinT86/linked-list-example)

## When to use it

Linked lists are a good data structure to use for things like ordered queues. When access to the list is done in ordered way. If random access to items is needed, a linked list can be inefficient due to having to run through each node.

They can also be efficient for adding data to the list. As each node stores the reference to the next node, inserting a new node at the start of the list or in the middle of the list, doesn't need to move or update the rest of the list.

## Summary

I've really enjoyed digging in to a data structure that I haven't used much. While a linked list might not be the best choice in every situation, I always like to add new tools to my tool belt. I'm looking forward to learning more about some other data structures.