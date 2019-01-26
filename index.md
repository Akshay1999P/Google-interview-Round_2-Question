package com.srpec.jdbc;
import java.sql.*;
import java.io.*;

public class JdbcApp01 {

	public static void main(String[] args) throws Exception{
		
		//Step 1
        Class.forName("oracle.jdbc.OracleDriver");
 
        //Step 2: Establish connection between java application and database
        //Connection conn=DriverManager.getConnection("driver url","username","password");
        
      Connection conn=DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe","system","1999");
      
      //Step 3: Create Statement object
      
      Statement s=conn.createStatement();
      
      BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
      System.out.println("Enter the Table you want to creat in database: ");
      String table=br.readLine();
      
      
      //Step 4: Create SQL Query
      
      String query = "create table "+table+"(Eno number(4) Primary key,Ename varchar2(15),Esal float(5),Eadd varchar2(15))";
      
      //Step 5: Execute SQL query
      
     // s.executeQuery(query);
      s.executeUpdate(query);
      
      System.out.println(table+" Create SUccessfull in Database");
      
      br.close();
      s.close();
      conn.close();
      
	}
}
