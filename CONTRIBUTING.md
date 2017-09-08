  private void jButton2ActionPerformed(java.awt.event.ActionEvent evt) {                                         
    
     
    
      if(newpass.equals(conpass))
      {
          updatingpass();
          
      }else{
          JOptionPane.showMessageDialog(this,"Password and Confirm Password doesn't match!!");
      }
     
    
    }                                        

    private void jButton1ActionPerformed(java.awt.event.ActionEvent evt) {                                         
SHARED_DATA o1=  new SHARED_DATA();
 String n= o1.getname();
usernametext.setText(n);

    }                                        

    private void quesbuttonActionPerformed(java.awt.event.ActionEvent evt) {                                           
      try
      {
        Class.forName("com.mysql.jdbc.Driver");
        Connection con =DriverManager.getConnection("jdbc:mysql:///viru","root","");
        String queryy="select securityques   from userdata where username ='"+usernametext.getText()+"'";
        PreparedStatement ps=con.prepareStatement(queryy);
        
        ResultSet rs=ps.executeQuery();
        
        while(rs.next())
        {
//         secureques=  rs.getString("securityques");
           securequeslbl.setText(rs.getString("securityques"));
        }
      
      } // try ends here
      catch(Exception e)
      {
          e.printStackTrace();
      }
     
    }                                          

    private void usernametextActionPerformed(java.awt.event.ActionEvent evt) {                                             
       
    }                                            
  public void updatingpass()
   {
       try {
        
                  Class.forName("com.mysql.jdbc.Driver");
           Connection conn= DriverManager.getConnection("jdbc:mysql:///viru","root","");
          
          PreparedStatement pst=conn.prepareStatement("update userdata set password='"+newpass+"' where username='"+usernametext.getText()+"', ");
    int rse;
    rse=pst.executeUpdate();
            
            
            if(rse>0)                                      
        {
            JOptionPane.showMessageDialog(this, "Data Updated sucessfully");
            conn.close();
         } //  if ends here 
            
        else        
        {
          JOptionPane.showMessageDialog(this, "data update  failed");
        }
            //  esle  ends here 
         
         } // try block ends her e
       catch (Exception e) {
             
           JOptionPane.showMessageDialog(this, "Exception occurs");
             
       e.printStackTrace();
         } // catch ends here 
