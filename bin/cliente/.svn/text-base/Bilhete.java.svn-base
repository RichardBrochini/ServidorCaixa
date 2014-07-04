package cliente;

import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.util.Vector;
import io.Arquivo;

public class Bilhete {
	private Vector <String> linhas;
	private BufferedReader in;
	private int total;
	public Bilhete(){
		try {
			this.in = new BufferedReader(new FileReader("saida.txt"));
			this.in.readLine();
			this.in.readLine();
		}catch (IOException e){

		}
	}
 
	public String removerLinha(){
        String str;
		try {
			if((str = this.in.readLine()) != null) {
				this.total++;
				return str;
			}else{
				this.total = -1;
				return "acabou";
			}
		}catch(IOException e) {
			e.printStackTrace();
		}
		this.total = -1;
		return null;			
	}
	
	public int getTotal(){
		return this.total;
	}
}