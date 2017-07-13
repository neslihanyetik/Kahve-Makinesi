package main;

import java.util.Scanner;

public class KahveMakinesi {
	// int [][][] d = {{{1,2},{2,3}},{{4,5},{6,7}}};
	static int[][] urunler = { { 5, 2 }, { 10, 3 }, { 2, 7 }, { 12, 1 }, { 10, 5 } };

	public static void main(String[] args) {
		boolean durum; 
		
		do{
			durum =SatinAlYonet();
		
		}while(durum);

	}

	public static void UrunGoster() {
		System.out.println(" Urunler:");
		System.out.println(" 	0 Kola Birim Fiyatı  "+urunler[0][1] +" Stok Adet  "+ urunler[0][0]);
		System.out.println(" 	1 Fanta Birim  Fiyatı   "+urunler[1][1] +" Stok Adet  "+ urunler[1][0]);
		System.out.println(" 	2 M.Suyu Birim  Fiyatı  "+urunler[2][1] +" Stok Adet  "+ urunler[2][0]);
		System.out.println(" 	3 Kahve Birim Fiyatı  "+urunler[3][1] +" Stok Adet  "+ urunler[3][0]);
		System.out.println(" 	4 Çay Birim  Fiyatı  "+urunler[4][1] +" Stok Adet  "+ urunler[4][0]);

	}

	public static boolean SatinAlYonet() {
		Scanner sc = new Scanner(System.in);
		UrunGoster();

		System.out.println(" Ne alacaksınız ?");
		int urun = sc.nextInt();

		System.out.println(" Kaç Tane Alacaksınız ?");
		int adet = sc.nextInt();

		System.out.println(" Para Yatırınız?");
		int yatirilanPara = sc.nextInt();

		if (AdetKontrol(urun, adet)) {
			if (FiyatKontrol(urun, adet, yatirilanPara)) {
				System.out.println("Urun Alma Başarılı");
				// Para Üstü Gösterilecek.
				StokDusme(urun, adet);
				
		
			}
		}
	 
		return StokAdetKontrol();
	}

	public static boolean StokAdetKontrol(){
		for (int i = 0; i < urunler.length; i++) {
			if(urunler[i][0]>0){
				return true;
			}
		}
		return false;
	} 
	
	public static void StokDusme(int urun, int adet) {
		int urunStokAdet = urunler[urun][0];
		urunler[urun][0] = urunStokAdet - adet;
	}

	public static boolean FiyatKontrol(int urun, int istenileAdet, int verilenPara) {
		int urunBirimFiyat = urunler[urun][1];
		int toplamTutar = urunBirimFiyat * istenileAdet;
		if (verilenPara >= toplamTutar) {
			return true;
		} else {
			System.out.println("Verdiğiniz Almak İstedikleriniz İçin Yeterli Değil");
			return false;
		}

	}

	public static boolean AdetKontrol(int urun, int istenileAdet) {
		int urunStokAdet = urunler[urun][0];
		if (urunStokAdet >= istenileAdet) {
			return true;
		} else {
			System.out.println("Stokda Yeterli Urun Yok");
			return false;
		}
	}

}
