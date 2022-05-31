# Secret_Number
Adivina el numero de cuatro digitos que la máquina piensa, tendrás pistas que te ayudarán a resolverlo más rápido, * si existe el número y esta en la misma posición y - si existe el número pero no se encuentra en su posición. La única condición es que ningún número se repite.

#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <stdbool.h>

int main()
{
	int ValorU[4];
	int NumeroSecreto;
	int V[4];
	int opc1 = 0;
	int opc2 = 0;
	bool e;
	int ganar;
	int turno;
	char res;

	printf("BIENVENIDO AL JUEGO 'SECRET NUMBER' ¿QUIERES CONOCER LAS REGLAS DEL JUEGO?\n[SI: 1 NO: 0]: ");
	scanf("%d", &opc1);
	system("cls");
	if(opc1 == 1){
		printf("EL JUEGO CONSISTE EN ADIVINAR UN NUMERO DE CUATRO DIGITOS, LAS UNICA CONDICION ES QUE NINGUNO DE LOS NUMEROS SE REPITE.");
		printf("\nTENDRAS PISTAS QUE TE AYUDARAN A ADIVINAR EL NUMERO:\n- EL ASTERISCO [*] TE INDICARA SI UN NUMERO EXISTE Y SI ESTA EN SU POSICION.");
		printf("\n- EL GUION [-] TE INDICARA QUE EL NUMERO EXISTE PERO QUE NO SE ENCUENTRA EN ESA POSICION.");
		printf("\n¿ENTENDISTE LAS REGLAS Y DESEAS CONTINUAR? [SI: 1 NO: 0]: ");
		scanf("%d", &opc2);
	}else{
		printf("HASTA LUEGO :D");
		return 0;
	}
	system("cls");
	if(opc2 == 1){
		for(int i = 0; i < 4; i++){
			srand((unsigned)time(0));
			do{
				NumeroSecreto = rand()%10;
				for(int x = 0; x < i; x++){
					if(V[x] == NumeroSecreto){
						e = true;
						break;
					}
				}
			}while(e);
			V[i]= NumeroSecreto;
		}
		printf("RESULTADO");
		for(int i = 0; i < 4; i++){
			printf("Numero Secreto: %d", &V[i]);
		}
		do{
			printf("Turno: %d", &turno);
			ValorU[0];
			ValorU[1];
			ValorU[2];
			ValorU[3];
			res = "";
			ganar = 0;
			for(int i = 0; i < 4; i++){
				for(int j = 0; j < 4; j++){
					if(V[i] == ValorU[j] && i == j){
						res += "*";
						ganar++;
						break;
					}else if(V[i] == ValorU[j]){
						res += "-";
						break;
					}
				}
			}
			printf("Pista: %c", &res);
			turno++;
		}while(ganar < 4 && turno <= 20);
		printf("\n");
		if(ganar == 4){
			printf("FELICIDADES :D HAS ADIVINADO EL NUMERO");
		}else{
			printf("SUERTE PARA LA PROXIMA :(");
		}
	}
	return 0;
}
