package agenda_telefonica;
import java.util.HashMap;
import java.util.ArrayList;
import java.io.*;

public class Agenda {

        HashMap<String, String> myContact = new HashMap<>();
        String[] arrayContacto;
        
        String inputFilename = "C:\\Users\\FTD\\Desktop\\ESCUELA\\4\\Programacion Orientada\\netbeans\\Actividad4\\src\\main\\java\\input.csv";
        String outputFilename = "C:\\Users\\FTD\\Desktop\\ESCUELA\\4\\Programacion Orientada\\netbeans\\Actividad4\\src\\main\\java\\output.csv";
        
        public Agenda(){
            //contactos = new ArrayList<Agenda>();
         }
        
        public void cargarContactosFile(){
            BufferedReader bufferedReader = null;
            BufferedWriter bufferedWriter = null;             
            
            try{
                bufferedReader = new BufferedReader (new FileReader (inputFilename));
                bufferedWriter = new BufferedWriter (new FileWriter (outputFilename));
                
                String line;
                while ((line = bufferedReader.readLine()) != null) {
                    System.out.println(line);
                    arrayContacto= line.split(",");
                    myContact.put(arrayContacto[0], arrayContacto[1]);
                                  
                }
            }    
            catch (IOException e){
                System.out.println("IOException catched while reading: " + e.getMessage());
            }   
            finally  {
                try  {
                    if (bufferedReader != null) {
                        bufferedWriter.close();
                    }
                }    
                catch (IOException e){
                    System.out.println("IOException catched while closing: " + e.getMessage());
                }    
            }
        }
        
        public void mostrar(){
            for (HashMap.Entry<String,String> entry : myContact.entrySet()){
            String key = entry.getKey();
            String value = entry.getValue();
            
            System.out.println("Listado");
            System.out.println(key + " " + value);
            
            }
        
        }
        
        public void addContacto() {
            System.out.println("Metodo AddContacto: ");
            myContact.put("5526331548", "Javier Vazquez");
        }
        
        public void actualizarContactosFile(){
            BufferedWriter bufferedWriter = null;
            
            try{
                bufferedWriter = new BufferedWriter (new FileWriter(outputFilename));
                
                String line;
                for (HashMap.Entry<String,String> entry : myContact.entrySet()){
                    String key = entry.getKey();
                    String value = entry.getValue();
                    
                    line = key + " , " + value;
                    bufferedWriter.write(line+ "\n");
                }        
                
            }
            catch(IOException e) {
                System.out.println("IOException catched while reading: " + e.getMessage());
            }    
            finally{
                try {
                    if (bufferedWriter != null){
                        bufferedWriter.close();
                    }
                }
                catch (IOException e){
                    System.out.println("IOException catched while closing: " + e.getMessage());
                }
            }
        }
        
        
        
        
        
}

