# SQL Dtabases tutorial

## Introduction

- Dbs are any collection of related info
- Database Management systems (DBMS) is a software to mnage the b
- CRUD = Creat Read Update Delte

## Core Concepts

- All tables have:
  - columns
    - single attributes
  - rows
    - individual entry of for the table
- You always want to have a primary key
  - Attribute which is not repeated
  - Is a unique identifier of rows
  - It can be whatever: string, number, etc.
- Types of keys
  - Segregate key:
    - is a key that has no real meaning in the real world
  - Natural key:
    - a key that has a purpose in the real world
  - Foreign key:
    - attribute that defines the relationships between entries:
      - Can be from the same table or other
    - Is a primary key from same table or another
  - Composite key:
    - key that is made of 2 attributes or more
    - Only together can they identify a single row

## SQL Basics

- Structure Query Language (SQL)
- used for interacting with relational DBMS
- SQL varies between each implementation but they are usually really alike
- Is a hybrid language:
- Data Query Language
  - USed to query
- Data Definition language
  - Used for definning database schemas
- Data Control Language
  - USed for controlling access to the data in the db
  - You can grant users permissions
- Data MAnipulation Language
  - Used for CRUD data from the db
- Queries:
  - is a set of instructions given to the DBMS, that tells the DBMS what do you want to retrieve
  - The goal is to get the data you want

