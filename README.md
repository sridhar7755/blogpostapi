# Blog Post API Assignment

Hello!

This repository contains everything that you need to complete your assignment.

Please take this seriously, because we do!  We carefully assess every assignment that is
turned in to determine if you have the qualities that we're looking for at NWEA.

# The Assignment

You are a DevOps engineer.  Your boss has requested that you build a blog post API.
You have been given a database schema by the DBA team that you will need to use to insert information into a SQLite database.
Create a repository on Github (do *not* fork this one) and add the code necessary to provide an API that will write single posts to the
database and retrieve a list of all posts from the database.  You should include a copy of the database in your repository.
It ought to work "out of the box".

# Requirements

1. You *must* use a scripting language (i.e., Perl, Python, Ruby, Go, Java, Node)
2. Shell scripting is *not* allowed for the assignment (i.e., Bash, Ksh, Zsh)
3. Your solution *must* be easily deployable and include a well documented process to do so.
4. Your solution *must* be checked into Github.  Do *not* submit a pull request to this repository.  Send us a link to *your* repository.
5. Please show your work.  We want to see multiple commits and see how you approached the problem.

# API Implementation

You will need to implement 2 API endpoints for this assignment.

1. An endpoint for POSTing a single blog post
  * Endpoint *must* be `/post`
  * Method *must* be `POST`
  * Content of the `POST` *must* be the `title` and `body` of the post
2. An endpoint for GETing all blog posts
  * Endpoint *must* be `/posts`
  * Method *must* be `GET`
  * There should be no content sent (this is a GET request)
  * Content received *must* be the `post_id`, `title`, and `body` of all posts in an array

All data exchanged with the API *must* be in JSON format.

# Included in the Repository

You will find a file called `blog.db` in the repository.  It is a SQLite database file and already includes the table you need for persisting blog post data.

When the API is used to POST a blog post it should be written to the database.  When a GET is called the API should retrieve all entries from the database.

# Last Words

Have fun!  If you don't like doing this assignment you probably won't like working here.  We like to code and we do a lot of automation.

We're looking forward to seeing your API in action!

JDBCExample.java
================

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.util.Scanner;
 
public class JDBCExample {
public static void main(String[] args) {
Scanner sc = new Scanner(System.in);
System.out.println("enter publisher id");
int publisherID = sc.nextInt();
System.out.println("enter publisher name");
String publisher_Name = sc.next();
 
System.out.println("enter author id");
int authorsID1 = sc.nextInt();
System.out.println("enter author firstname name");
String firstName = sc.next();
System.out.println("enter author lastName name");
String lastName = sc.next();
 

 
try{
Class.forName("com.mysql.jdbc.Driver");
Connection con=DriverManager.getConnection("jdbc:mysql://localhost/books","root","nooraen");
 
PreparedStatement stmt = con.prepareStatement("insert into publishers values (?, ?)");
stmt.setInt(1, publisherID);
stmt.setString(2, publisher_Name);
stmt.executeUpdate();
 
stmt = con.prepareStatement("insert into authors values(?, ?, ?)");
stmt.setInt(1, authorID);
stmt.setString(2, firstName);
stmt.setString(3, lastName);
stmt.executeUpdate();
 
 
stmt.close();
System.out.println("Inserted records into the table...");
}
catch(Exception e)
{
System.out.println(e);
}
}
}

