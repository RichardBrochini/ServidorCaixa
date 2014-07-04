package servidor;

import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.ServerSocket;
import java.util.Vector;

import cliente.Bilhete;
import cliente.Cliente;
import constantes.Constantes;

public class Servidor {
	private ServerSocket conexao;
	private OutputStream saida;
	private InputStream  entrada;
	private Vector <Cliente> clientes;
	public  Bilhete bilhete;

	public Servidor(){
		try{
			this.bilhete  = new Bilhete();
			this.conexao  = new ServerSocket(Constantes.PORTA,100);
			this.clientes = new Vector();
			Ativar ativa = new Ativar();
			ativa.start();
		}catch(IOException e){
			e.printStackTrace();
			System.out.println("Não foi possivel iniciar o servidor!");
			System.exit(1);
		}
	}

	public void aceitar(int i){
		try{
			Cliente cliente = new Cliente(this.conexao.accept(),this.clientes,this.bilhete);
			this.clientes.add(cliente);
			cliente.start();
		}catch (IOException e){
			e.printStackTrace();
		}
	}
}
