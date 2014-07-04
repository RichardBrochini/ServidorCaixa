package cliente;

import java.net.*;
import java.util.Scanner;
import java.util.Formatter;
import java.util.Vector;
import java.io.*;

import constantes.Constantes;
import constantes.Resultado;

public class Cliente extends Thread{
	private Socket conexao;
	private Formatter  saida;
	private Scanner entrada;
	public  Vector <Cliente> clientes;	
	public  Bilhete bilhete;
	public  boolean terminou = false;
	
	public Cliente(Socket conexao,Vector <Cliente> clientes,Bilhete bilhete){
		this.bilhete  = bilhete;
		this.conexao  = conexao;
		this.clientes = clientes;
		try{
			this.entrada = new Scanner(this.conexao.getInputStream()).useDelimiter("\0");
			this.saida   = new Formatter(this.conexao.getOutputStream());
		}catch (IOException e){
			e.printStackTrace();
		}
	}
	
	public void enviarMsg(String msg){
		msg = msg+"\0"; 
		this.saida.format(msg);
		this.saida.flush();
	}

	public String receberMsg(){
		String linha = "";
		if(this.entrada.hasNext()){
			linha = this.entrada.next();
			return linha;									
		}else{
			return "";
		}
	}

	public void run(){
		int sena=0,quina=0,quadra=0;
		Vector <String> senas = new Vector();
		while(!this.conexao.isClosed()){
			if(Constantes.comeca){
				String msg = this.receberMsg();
				if(msg.equals("0")){
					String numeros = "";
					for(int i = 0;i<6;i++){
						numeros = numeros+String.valueOf(Constantes.NUMEROS[i])+",";						
					}
					System.out.println("envio numero sorteado: "+numeros);
					this.enviarMsg(numeros);
				}else{
					if(msg.equals("10")){
						this.terminou = true;
						int contador = 0;
						//verifica se é o ultimo cliente a terminar
						for(int i = 0;i<this.clientes.size();i++){
							if(this.clientes.get(i).terminou){
								contador++;
							}
						}
						if(contador >= (this.clientes.size()-1)){
							if(this.bilhete.getTotal()==-1){	
								if(Resultado.imprir){
									Resultado.imprir = false;
									System.out.println("sena   = "+Resultado.sena);	            				
									System.out.println("quina  = "+Resultado.quina);	            	
									System.out.println("quadra = "+Resultado.quadra);
									System.out.println("uf dos ganhadores da sena:");
									for(int i = 0;i<Resultado.senas.size();i++){
										System.out.println("uf  = "+Resultado.senas.get(i));
									}
								}else{
									break;
								}
								//System.out.println("total  = "+total);	            								
							}													
						}else{
							break;
						}
					}else{
						if(msg.equals("1")){
							this.enviarMsg(this.bilhete.removerLinha());
						}else{
							if(Integer.parseInt(msg.split(",")[0].split(";")[0])>0){
								Resultado.senas.add(msg.split(",")[0].split(";")[1]);
								//senas.add(msg.split(",")[0].split(";")[1]);
						    }
							Resultado.sena   = Resultado.sena+Integer.parseInt(msg.split(",")[0].split(";")[0]);
							Resultado.quina  = Resultado.quina+Integer.parseInt(msg.split(",")[1]);;
							Resultado.quadra = Resultado.quadra+Integer.parseInt(msg.split(",")[2]);							

							//sena   = sena+Integer.parseInt(msg.split(",")[0].split(";")[0]);
							//quina  = quina+Integer.parseInt(msg.split(",")[1]);
							//quadra = quadra+Integer.parseInt(msg.split(",")[2]);
						}						
					}
				}
			}
			/*for(int i=0;i<this.clientes.size();i++){
				this.clientes.get(i).enviarMsg(msg);
			}*/
		}
	}
}