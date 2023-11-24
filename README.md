import java.util.ArrayList; import java.util.Scanner;

class Buku { String judul; String pengarang; boolean tersedia;

public Buku(String judul, String pengarang) {
    this.judul = judul;
    this.pengarang = pengarang;
    this.tersedia = true;
}
}

class Peminjam { String nama;

public Peminjam(String nama) {
    this.nama = nama;
}
}

class Perpustakaan { ArrayList daftarBuku = new ArrayList<>(); ArrayList daftarPeminjam = new ArrayList<>();

public void tambahBuku(String judul, String pengarang) {
    Buku buku = new Buku(judul, pengarang);
    daftarBuku.add(buku);
}

public void daftarBuku() {
    System.out.println("Daftar Buku:");
    System.out.println("1. laskar pelangi:10");
    System.out.println("2.layangan putus :10");
    System.out.println("3.biologi :10");
    System.out.println("4. fisika :10");
    System.out.println("5. sistem operasi :10");
    System.out.println("6.psikologi :10");
    System.out.println("7. matematika :10 ");
    System.out.println("8. shinchan :10 ");
    for (Buku buku : daftarBuku) {
        System.out.println(buku.judul + " - " + buku.pengarang + " - " + (buku.tersedia ? "Tersedia" : "Dipinjam"));
    }
}

public void pinjamBuku(String judul, String peminjam) {
    for (Buku buku : daftarBuku) {
        if (buku.judul.equals(judul) && buku.tersedia) {
            buku.tersedia = false;
            Peminjam p = new Peminjam(peminjam);
            daftarPeminjam.add(p);
            System.out.println("Buku " + judul + " berhasil dipinjam oleh " + peminjam);
            return;
        }
    }
    System.out.println("Buku " + judul + " tersedia untuk dipinjamkan.");
}

public void kembalikanBuku(String judul) {
    for (Buku buku : daftarBuku) {
        if (buku.judul.equals(judul) && !buku.tersedia) {
            buku.tersedia = true;
            System.out.println("Buku " + judul + " berhasil dikembalikan.");
            return;
        }
    }
    System.out.println("Buku " + judul + " buku sudah tersedia .");
}
}

public class Main { public static void main(String[] args) { Perpustakaan perpustakaan = new Perpustakaan(); perpustakaan.tambahBuku("laskar pelangi", "andrea hirata"); perpustakaan.tambahBuku("layangan putus", "manoj punjanbi"); perpustakaan.tambahBuku("biologi", "bse"); perpustakaan.tambahBuku("fisika", "airlangga "); perpustakaan.tambahBuku("sistem operasi", "andrew s tanebaum "); perpustakaan.tambahBuku("psikologi", "daniel kayes "); perpustakaan.tambahBuku("matematika", "airlangga "); perpustakaan.tambahBuku("shincan", "yoshito usui");

    Scanner scanner = new Scanner(System.in);
    int pilihan;

    do {
        System.out.println("\nMenu:");
        System.out.println("1. Daftar Buku");
        System.out.println("2. Pinjam Buku");
        System.out.println("3. Kembalikan Buku");
        System.out.println("0. Keluar");

        System.out.print("Pilih menu (0-3): ");
        pilihan = scanner.nextInt();

        switch (pilihan) {
            case 1:
                perpustakaan.daftarBuku();
                break;
            case 2:
                System.out.print("Masukkan judul buku yang ingin dipinjam:fisika");
                System.out.print("Masukkan jumlah buku yang ingin di pinjam:1 ");
                System.out.print("jumlah buku yang masih tersedia:4 ");
                String judulPinjam = scanner.next();
                System.out.print("Masukkan nama peminjam:  ");
                String namaPeminjam = scanner.next();
                perpustakaan.pinjamBuku(judulPinjam, namaPeminjam);
                break;
            case 3:
                System.out.print("Masukkan judul buku yang ingin dikembalikan: ");
                String judulKembali = scanner.next();
                perpustakaan.kembalikanBuku(judulKembali);
                break;
            case 0:
                System.out.println("Program selesai.");
                break;
            default:
                System.out.println("Pilihan tidak valid. Silakan coba lagi.");
        }

    } while (pilihan != 0);

    scanner.close();
}
}
