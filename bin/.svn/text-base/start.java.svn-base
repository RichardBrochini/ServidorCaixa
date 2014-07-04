import servidor.Servidor;
import io.Arquivo;
import constantes.Constantes;

public class start {
	public static void main(String[] args) {
		Constantes.setConst(Arquivo.carregar("conf"));
		Servidor s = new Servidor();
		for(int i = 0;;i++){
			System.out.println("Total de maquinas: "+i);
			s.aceitar(i);
		}
	}
}