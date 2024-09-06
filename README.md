import java.util.ArrayList;
import java.util.Scanner;

// Class untuk menyimpan detail produk
class Produk {
    String namaProduk;
    int jumlah;
    double harga;

    public Produk(String namaProduk, int jumlah, double harga) {
        this.namaProduk = namaProduk;
        this.jumlah = jumlah;
        this.harga = harga;
    }

    // Menghitung total harga per produk
    public double totalHarga() {
        return jumlah * harga;
    }
}

public class PenjualanSwalayan {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Produk> daftarPenjualan = new ArrayList<>();
        boolean lanjut = true;

        // Loop untuk menambahkan produk ke dalam tabel penjualan
        while (lanjut) {
            System.out.println("Masukkan Nama Produk:");
            String namaProduk = scanner.nextLine();

            System.out.println("Masukkan Jumlah Produk:");
            int jumlah = scanner.nextInt();

            System.out.println("Masukkan Harga Produk:");
            double harga = scanner.nextDouble();
            scanner.nextLine(); // Membersihkan buffer

            // Menambahkan produk ke daftar
            daftarPenjualan.add(new Produk(namaProduk, jumlah, harga));

            System.out.println("Apakah ingin menambah produk lagi? (y/n):");
            String jawaban = scanner.nextLine();
            if (jawaban.equalsIgnoreCase("n")) {
                lanjut = false;
            }
        }

        // Menampilkan hasil penjualan
        System.out.println("\nTabel Penjualan Swalayan:");
        System.out.println("===========================================");
        System.out.println("Nama Produk\tJumlah\tHarga\tTotal");
        System.out.println("===========================================");

        double totalPenjualan = 0;

        for (Produk produk : daftarPenjualan) {
            double total = produk.totalHarga();
            System.out.printf("%s\t\t%d\t\t%.2f\t%.2f\n", produk.namaProduk, produk.jumlah, produk.harga, total);
            totalPenjualan += total;
        }

        System.out.println("===========================================");
        System.out.printf("Total Penjualan: %.2f\n", totalPenjualan);
    }
}
