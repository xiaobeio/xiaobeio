- 👋 Hi, I’m @xiaobeio
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
xiaobeio/xiaobeio is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
package com;

import java.sql.*;
import java.util.Scanner;

public class DataOperator {
    public void querySelect(String strsql) {
        Connection con = null;//杩炴帴
        Statement st = null;//
        ResultSet rs = null;

        String strurl = "jdbc:mysql://localhost:3306/studentuser";
        String strusername = "root";
        String strpassword = "root";


        //
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            //
            con = DriverManager.getConnection(strurl, strusername, strpassword);
            //鍒涘缓statemnt瀵硅薄
            st = con.createStatement();
            //SQL璇?

            //鎵цSQL 杩斿洖sz
            rs = st.executeQuery(strsql);
            while (rs.next()) {
                //绉诲姩鍒颁笅涓€鏉?
                //鑾峰彇鎸囧畾璁板綍
                int id = rs.getInt(1);
                String username = rs.getString("name");
                String sex = rs.getString("sex");
                System.out.println(id + "," + username + "," + sex);
            }
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            //閲婃斁璧勬簮
            {
                try {
                    if (rs != null) rs.close();
                    if (st != null) st.close();
                    if (con != null) con.close();
                } catch (SQLException throwables) {
                    throwables.printStackTrace();
                }
            }
        }


    }

    public static void main(String[] args) {
        System.out.println("************瀛︾敓绠＄悊绯荤粺************");
        System.out.println("1,鏌ヨ瀛︾敓淇℃伅");
        System.out.println("1,淇敼瀛︾敓淇℃伅");
        System.out.println("1,娣诲姞瀛︾敓淇℃伅");
        System.out.println("1,鍒犻櫎瀛︾敓淇℃伅");
        System.out.println("1,鎻愬嚭瀛︾敓淇℃伅绠＄悊绯荤粺");
        System.out.println("**********************************");
        DataOperator dt = new DataOperator();
        //閫夋嫨鍔熻兘
        Scanner sc = new Scanner(System.in);
        int i = sc.nextInt();
        while (i != 0) {
            if (i == 1) {
                String strsql = "select * from student";
                dt.querySelect(strsql);
            } else if (i == 2) {

            } else if (i == 3) {


            } else if (i == 4) {


            }
            System.out.println("缁х画鎿嶄綔");
            i = sc.nextInt();

            System.out.println("閫€鍑虹郴缁?);

        }
    }
}
