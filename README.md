# Posicion-Alfil
Este programa indica los posibles movimientos de un alfil en un tablero de ajedrez según una posición dada.
import java.util.Scanner;

public class posicion_alfil {
	
	static Scanner sc= new Scanner(System.in);
	
	public static void rellenar (int ma[][]) { //2. Rellenamos el tablero con 0
		
		for (int i = 0; i < ma.length; i++) {
			for (int j = 0; j < ma[i].length; j++) {
				ma[i][j]=0;
			}
		}
	}
	
	public static void imprimir(int ma[][], String f[], String c[]) { //3. Imprimimos el tablero con la forma
		
		System.out.printf("%4s","");
		
		for (int i = 0; i < c.length; i++) {
			System.out.printf("%6s", c[i]);
		}
		System.out.println("");
		System.out.println("");
		
		for (int i = 0; i < ma.length; i++) {
			
			System.out.printf("%4s", f[i]);
			
			for (int j = 0; j < ma[i].length; j++) {
				System.out.printf("%6d", ma[i][j]);
			}
			
			System.out.println("");
			
		}
		
	}

	public static void main(String[] args) {
	
		//1. Primero definimos el tablero con esta matriz y estos dos vectores
		int [][] tb= new int [8][8];
		String [] filas= {"8","7","6","5","4","3","2","1"};
		String [] columnas= {"a","b","c","d","e","f","g","h"};
		
		int posicionFila, posicionColumna;
		
		rellenar(tb);
		System.out.println("Este es un programa que, según una posición dada, indicará los posibles movimientos de un alfil");
		System.out.println("Dado el siguiente tablero:");
		System.out.println("");
		imprimir(tb, filas, columnas);
		System.out.println("");
		System.out.println("Indique la posición inicial del alfil");
		//4. Pedimos la posición inicial
		String posicion=sc.nextLine();
		
		//5. Ahora debemos transformar la posición 
		posicionColumna=posicion.charAt(0)-'a';
		posicionFila=8-(posicion.charAt(1)-'0'); //Marcamos que en el 1 es la posicion de la matriz 0 pero le restamos 8 porque esta invertido
		
		
		tb[posicionFila][posicionColumna]=1; //Establecemos el alfil en el tablero en la posición indicada
		
		System.out.println("A continuación, los posibles movimientos del alfil siendo 1, su posición actual y 2 sus posibles localizaciones ");
		for (int filaActual = 0; filaActual < 8; filaActual++) { //Con estos for vamos a recorrer todo el tablero por filas y columnas y comprobar el if
			for (int columnaActual = 0; columnaActual <8; columnaActual++) {
				
				if (Math.abs(posicionFila-filaActual)== Math.abs(posicionColumna-columnaActual) //Si la diferencia entre la fila indicada y la fila que se esta comprobando es igual
						&& !(posicionFila==filaActual && posicionColumna==columnaActual)) { // a la diferencia entre la columna indicada y la columna comprobada y si no son iguales
					
					char col=(char)('a'+columnaActual); //Entonces se dará la posición
					int fil=8-filaActual;
					System.out.println(col+" "+fil);
					tb[filaActual][columnaActual]=2; //Y se marcará con un 2 en el tablero
					
					
				}
			}
		}
		
		imprimir(tb,filas,columnas);
	

	}
}
