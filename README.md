#include <stdio.h>
#include <string.h>
#define size_data 10
float add(float first_num1, float second_num1){
	float result1;
	result1=first_num1+second_num1;
	return result1;
}
float substract(float first_num2, float second_num2){
	float result2;
	result2=first_num2-second_num2;
	return result2;
}
float multiply(float first_num3, float second_num3){
	float result3;
	result3=first_num3*second_num3;
	return result3;
}
float div(float first_num4, float second_num4){
	float result4;
	result4=first_num4/second_num4;
	return result4;
}
void menu_utama(){
		printf("\t\t\tMenu Pilihan :\n");
		printf("\t\t\t1. Kalkulator Sederhana\n");
		printf("\t\t\t2. Mencari nilai mean, median, modus\n");
		printf("\t\t\t3. Sorting data\n");
		printf("\t\t\t4. Menghilangkan duplikasi\n");
		printf("\t\t\t5. Exit\n\n");
}

int main(){
	char ulang[1];
	char username[10];
	char password[10];
	int i, j, k=1, x=0;
	int data[size_data]={25,50,65,70,50,30,60,70,20,20};
	int angka_modus[10];
	int banyaknya[10];
			
	printf("\t\t\tSelamat Datang di Program Ajaib AMV\n");
	printf("\t\t\t===================================\n");
	printf("\t\t\t\tbikinan goldyTW\n\n");
	
	printf("masukkan username anda: ");
	scanf("%s",&username);
	printf("masukkan password anda: ");
	scanf("%s",&password);
	system("cls");
	if ((strcmp(username,"AMV")==0)&&(strcmp(password,"ju4r4ju4r4")==0)){
	do{
		int pilihan, pilihan2;
		float bil1, bil2;
		float hasil_tambah, hasil_kurang, hasil_kali, hasil_bagi;
		
		menu_utama();
		printf("\t\t\tpilihan (masukkan angka 1-5): ");
		scanf("%d", &pilihan);
		
		if (pilihan==1){
			system("cls");
			printf("Pilih operasi\n");
			printf("1. Tambah\n");
			printf("2. Kurang\n");
			printf("3. Kali\n");
			printf("4. Bagi\n");
			printf("pilihan (masukkan angka 1-4): ");
			scanf("%d", &pilihan2);
			
			if (pilihan2>=1 && pilihan2<=4){
				printf("Masukkan bilangan pertama: ");
				scanf("%f", &bil1);
				printf("Masukkan bilangan kedua: ");
				scanf("%f", &bil2);
				
				if (pilihan2==1){
					hasil_tambah=add(bil1, bil2);
					printf("Hasil penjumlahan adalah: %.2f", hasil_tambah);
				}
				else if (pilihan2==2){
					hasil_kurang=substract(bil1, bil2);
					printf("Hasil pengurangan adalah: %.2f", hasil_kurang);
				}
				else if (pilihan2==3){
					hasil_kali=multiply(bil1, bil2);
					printf("Hasil perkalian adalah: %.2f", hasil_kali);
				}
				else if (pilihan2==4){
					hasil_bagi=div(bil1, bil2);
					printf("Hasil pembagian adalah: %.2f", hasil_bagi);
				}
				else{
					printf("tidak ada pilihan!");
				}
			}
		}
		else if (pilihan==2){
			system("cls");
			for (i=0; i<size_data; i++){
				for(j=i+1; j<size_data; j++){
					if (data[i]>data[j]){
						int temp;
						temp=data[j];
						data[j]=data[i];
						data[i]=temp;	
					}
				}
			}
			printf("Data: \n[");
			for (i=0; i<size_data-1; i++){
				printf(" %d,",data[i]);
			}
			printf(" %d]",data[size_data-1]);
			
			int sum=0;
			for (i=0; i<size_data; i++){
				sum = sum+data[i];
			}
			printf("\n\nmean   = %d", sum/size_data);
			
			int mid_sum;
			mid_sum= data[4]+data[5];
			printf("\n\nmedian = %d", mid_sum/2);
			
			printf("\n\nmodus = ");
			//modus
			//mencari jumlah bilangan yg muncul
			for (i=0; i<size_data; i++){
				banyaknya[i]=0;
				for (j=i+1; j<size_data; j++){
					if (data[i]==data[j]){
						banyaknya[i]++;
					}
				}
			}
			//menentukan yang paling sering muncul
			for (i=0; i<size_data; i++){
				if (banyaknya[i]>k){
					k=banyaknya[i];
				}
			}
			//menentukan jika modus lebih dari 1
			for (i=0; i<size_data; i++){
				if (x==0){
					angka_modus[x]=0;
				}
				else{
					angka_modus[x]=angka_modus[x-1];
				}
				if (banyaknya[i]==k){
					if (data[i]!=angka_modus[x]){
						angka_modus[x]=data[i];
						x++;
					}
				}
			}
			
			//apabila ga ada modus
			int z=0;
			for (i=0; i<size_data; i++){
				if (banyaknya[i]==k){
					z++;
				}
			}
			if (z==size_data){
				x=0;
			}
			
			if (x==0)
				printf("\n\ntidak ada modus\n");
			else{
				int u;
				for (u=0; u<x-1; u++){
					if (x==1){
						printf("\n\nmodus hanya 1");
					}
				printf("%d, ", angka_modus[u]);
				}
				printf("%d", angka_modus[x-1]);
			}
		}
		else if (pilihan==3){
			system("cls");
			for (i=0; i<size_data; i++){
				for(j=i+1; j<size_data; j++){
					if (data[i]>data[j]){
						int temp;
						temp=data[j];
						data[j]=data[i];
						data[i]=temp;	
					}
				}
			} 
			printf("Data yang terurut: \n ");
			for (i=0; i<size_data;i++){
				printf("%d ", data[i]);
			}
			
		}
		else if(pilihan==4){
			system("cls");
			printf("Data tidak terduplikasi: \n");
			for (i=0; i<size_data; i++){
				for(j=i+1; j<size_data; j++){
					if (data[i]>data[j]){
						int temp;
						temp=data[j];
						data[j]=data[i];
						data[i]=temp;	
					}
				}
			}  
			
			for (i=0; i<size_data; i++){
				if(data[i]!=data[i+1]){
					printf("%d ",data[i]);
				}
			}
		}
		else if (pilihan==5){
			break;
		}
		else{
			printf("\ntidak ada pilihan!");
		}
			
		printf("\n\napakah anda ingin menggunakan program ini lagi? (Y/N) ");
		scanf("%s", &ulang);
		system("cls");
	}
	while((strcmp(ulang, "Y")==0) || (strcmp(ulang, "y")==0));
	printf("\nTerimakasih telah menggunakan program ini. Have a nice day!");
	}
	else{
		printf("username atau password anda salah!");
	}
	return 0;
}
