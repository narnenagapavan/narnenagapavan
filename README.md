- 👋 Hi, I’m @narnenagapavan
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
narnenagapavan/narnenagapavan is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import javax.swing.JOptionPane;
/**
*
* @author bagong
*/
public class ClassDB {
    private static Connection koneksi;
    public static Connection getkoneksi() {
        if (koneksi==null) {
            try {
                String url=new String();
                String user=new String();
                String password=new String();
                url="jdbc:mysql://localhost:3306/snake";
                user="root";
                password="";
                DriverManager.registerDriver(new com.mysql.jdbc.Driver());
                koneksi=DriverManager.getConnection(url,user,password);
               // JOptionPane.showMessageDialog(null,"Koneksi Berhasil");
            }catch (SQLException t) {
                JOptionPane.showMessageDialog(null,"Error membuat koneksi");
            }
        }
     return koneksi;
    }
}
private void nama(){
        Nama = JOptionPane.showInputDialog(this, "Please Input Your Name:");
        if (Nama == null) {
        System.exit(0);
        }
        else{
            if(Nama.equals("")){
        JOptionPane.showMessageDialog(this,"Name Already Exist!");
        nama();
            }
            else{
                try{
              Connection c=ClassDB.getkoneksi();
        Statement st=(Statement)c.createStatement();
        String ceknama="Select * from score where nama = '" + Nama.toString()+"'";
            ResultSet r=st.executeQuery(ceknama);
            if (r.next()){      
                    return;    
            }
            else{
                 try {          
            st.executeUpdate("Insert into score(nama) values('" + Nama.toString() + "')");        
                 }  
                 catch(Exception e){
            System.out.println(e);
        }  
            }
        
         }catch(Exception e){
             System.out.println(e);
         }      
       }
        
    }
    
    }
