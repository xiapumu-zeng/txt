<%@ page language="java" pageEncoding="utf-8"%>
<%@page import="dao.BaseDao"%>
<html>
<body>
    <%
        if ("POST".equals(request.getMethod())) {
            request.setCharacterEncoding("utf-8");
            String id = request.getParameter("txtId");
            String name = request.getParameter("txtUser");
            String major = request.getParameter("txtMajor");
            
            BaseDao dao = new BaseDao();
            String sql = "INSERT INTO student VALUES('"+id+"','"+name+"','"+major+"')";
            int count = dao.excuteUpdate(sql);
            String msg = count==1 ? "新增成功" : "新增不成功";
    %>
            <script>alert('<%=msg%>');location.href='index.jsp';</script>
    <%
        } else {
    %>
            <form method="post">
                学号:<input name="txtId"><p>
                姓名:<input name="txtUser"><p>
                专业:<input name="txtMajor"><p>
                <input type="submit" value="注 册">
                <input type="reset" value="取消">
            </form>
    <%
        }
    %>
</body>
</html>

和

package dao;
import java.sql.*;

public class BaseDao {
    private String url = "jdbc:mysql://localhost:3306/kkp";
    private String user = "root";
    private String password = "123456";

    public Connection getConnection() {
        Connection conn = null;
        try {
            Class.forName("com.mysql.jdbc.Driver");
            conn = DriverManager.getConnection(url, user, password);
        } catch (Exception e) {e.printStackTrace();}
        return conn;
    }
    public void closeAll(Connection conn, Statement stmt, ResultSet rs) {
        try {
        if(rs!=null)rs.close();
        if(stmt!=null)stmt.close();
        if(conn!=null)conn.close();}
        catch (SQLException e) {
        	e.printStackTrace();}
    }

    public int excuteUpdate(String sql) {
        Connection conn = null;
        Statement stmt = null;
        int count = 0;
        try {
            conn = getConnection();
            stmt = conn.createStatement();
            count = stmt.executeUpdate(sql);
        } catch (Exception e) {e.printStackTrace();}
        finally {closeAll(conn, stmt, null);}
        return count;
    }
}
