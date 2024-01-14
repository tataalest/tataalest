#include <iostream>
#include <iomanip>
#include <string>

using namespace std;

int pilihan, pembuatanakun, presensi, jammasuk, jamkeluar;
string namapengunjung, keperluan, tanggalkunjungan;
string username, password, x;
char memilikiakun;
int percobaanLogin = 0;
int keluarmenuUtama;

struct Jadwal
{
    string tanggal;
    string waktu;
    string lokasi;
    string praktikum;
    string penanggungJawab;
    string ketersediaan;
};

// Fungsi untuk menampilkan menu utama
void tampilkanMenuUtama()
{
    cout << endl;
    cout << "----------------  M  E  N  U  ----------------\n";
    cout << "1. Presensi \n";
    cout << "2. Jadwal \n";
    cout << "3. Kontak Penanggung Jawab \n";
    cout << "4. Peraturan Laboratorium\n";
    cout << "5. Keluar\n";
}

// Fungsi untuk menampilkan kode QR
void tampilkanPresensi()
{
    cout << endl;
    cout << "------------------------------------------------\n";
    cout << "               MENU PRESENSI \n";
    cout << "------------------------------------------------\n";
    cout << "1. Presensi Masuk \n";
    cout << "2. Presensi Keluar \n";
    cout << "Masukkan Pilihan : ";
    cin >> presensi;
    switch (presensi)
    {
    case 1:
        cout << "Masukkan Nama Anda         : ";
        cin.ignore();
        getline(cin, namapengunjung);
        cout << "Masukkan Tanggal Kunjungan : ";
        getline(cin, tanggalkunjungan);
        cout << "Masukkan Jam Masuk         : ";
        cin >> jammasuk;
        cout << "Masukkan Keperluan         : ";
        cin.ignore();
        getline(cin, keperluan);

        cout << endl;
        cout << "------------------------------------------------\n";
        cout << "             PRESENSI MASUK \n";
        cout << "------------------------------------------------\n";
        cout << "Nama              : " << namapengunjung;
        cout << endl;
        cout << "Tanggal Kunjungan : " << tanggalkunjungan;
        cout << endl;
        cout << "Jam Masuk         : " << jammasuk;
        cout << endl;
        cout << "Keperluan         : " << keperluan;
        cout << endl;
        break;

    case 2:
        cout << "Masukkan Nama Anda        : ";
        cin.ignore();
        getline(cin, namapengunjung);
        cout << "Masukkan Tanggal Kunjungan : ";
        getline(cin, tanggalkunjungan);
        cin.ignore();
        cout << "Masukkan Jam Keluar         : ";
        cin >> jamkeluar;
        cin.ignore();

        cout << endl;
        cout << "------------------------------------------------\n";
        cout << "             PRESENSI KELUAR \n";
        cout << "------------------------------------------------\n";
        cout << "Nama              : " << namapengunjung;
        cout << endl;
        cout << "Tanggal Kunjungan : " << tanggalkunjungan;
        cout << endl;
        cout << "Jam Keluar        : " << jamkeluar << endl;
        break;

    default:
        cout << "Pilihan tidak valid." << endl;
        break;
    }
}

// Fungsi untuk menampilkan jadwal laboratorium
void tampilkanJadwalLaboratorium()
{
    cout << endl;
    cout << "Jadwal Pemakaian Laboratorium \n";
    cout << "____________________________________________________________________________________________________________________________________ \n";
    cout << "|     Tanggal     |     Waktu     |     Lokasi      |        Praktikum yang sedang Dilakukan      | Penanggung Jawab | Ketersediaan |\n";
    cout << "____________________________________________________________________________________________________________________________________\n";
    cout << "\n";
    cout << "| 1 Februari 2024 | 07.00 - 10.00 | Lab pr. kimia 1 |                   -                         |      Renjana     |    Tersedia  |\n ";
    cout << "\n";
    cout << "|   3 maret 2024  | 18.00 - 21.00 | Lab pr. kimia 2 |  Penanganan bahaya kimia dalam pratikum      |      Haikal      |    Tidak    |\n ";
    cout << "\n";
    cout << "|  12 maret 2024  | 06.00 - 09.00 | Lab pr. kimia 1 |                    -                         |      Nana        |   Tersedia  |\n ";
    cout << "\n";
    cout << "|15 Februari 2024 | 09.00 - 12.00 | Lab pr. kimia 2 |    Resiko kesehatan penggunaan bahan kimia   |      Jevano      |    Tidak    |\n ";
    cout << "\n";
    cout << "| 23 Januari 2024 | 13.00 - 16.00 | Lab pr. kimia 1 |  Pengaruh paparan bahan kimia bagi kesehatan |       Mark       |    Tidak    |\n ";
    cout << "\n";
}

// Fungsi untuk melakukan pencarian binary pada data jadwal berdasarkan tanggal
int sequentialSearchJadwal(Jadwal array[], int n, string key)
{
    for (int i = 0; i < n; i++)
    {
        if (array[i].tanggal == key)
        {
            return i; // Mengembalikan indeks jika nama ditemukan
        }
    }
    return -1; // Mengembalikan -1 jika nama tidak ditemukan
}

// Fungsi untuk menampilkan nomor kontak
void tampilkanNomorKontak()
{
    cout << endl;
    cout << "------------------------------------------------\n";
    cout << "|         KONTAK PENANGGUNG JAWAB              |\n";
    cout << "------------------------------------------------\n";
    cout << "| No |       Nama       |      No Telepon      |\n";
    cout << "------------------------------------------------\n";
    cout << "| 1. |       Mark       |     081999080213     |\n";
    cout << "| 2. |      Renjana     |     082300200356     |\n";
    cout << "| 3. |      Jevano      |     083204000258     |\n";
    cout << "| 4. |      Haikal      |     082000606074     |\n";
    cout << "| 5. |       Nana       |     081300028077     |\n";
    cout << "------------------------------------------------\n";
}

// Fungsi untuk mencari nomor kontak berdasarkan nama
int sequentialSearch(string arr[], int panjang, string key)
{
    for (int i = 0; i < panjang; i++)
    {
        if (arr[i] == key)
        {
            return i; // Mengembalikan indeks jika nama ditemukan
        }
    }
    return -1; // Mengembalikan -1 jika nama tidak ditemukan
}

// Fungsi untuk menampilkan peraturan laboratorium
void tampilkanPeraturanLaboratorium()
{
    cout << endl;
    cout << "Berikut Peraturan Laboratorium yang Wajib ditaati\n";
    cout << "1. Pengguna laboratorium wajib menggunakan jas laboratorium serta Alat Pelindung Diri (APD) lengkap.\n";
    cout << "2. Mengisi buku kunjungan laboratorium.\n";
    cout << "3. Mengetahui fasilitas laboratorium, mengenal dan berkoordinasi dengan koordinator laboratorium.\n";
    cout << "4. Menyimpan barang bawaan didalam loker yang telah disediakan.\n";
    cout << "5. Tidak dibenarkan membawa makanan dan minuman, merokok dan berhias di dalam laboratorium.\n";
    cout << "6. Pengguna laboratorium tidak diperbolehkan bercanda selama praktikum\n";
    cout << "7. Apabila mengalami kondisi yang tidak aman, kecelakaan atau kerusakan alat segera melapor kepada petugas laboratorium.\n";
    cout << "8. Ikut menjaga dan merawat fasilitas laboratorium.\n";
    cout << "9. Jika terjadi kebakaran, singkirkan ataujauhkan semua bahan atau barang dari api dan gunakan alat pemadam kebakaran yang tersedia.\n";
    cout << "10. Mematuhi dan memenuhi standar kerja di laboratorium.\n";
}

// fungsi untuk mengurutkan peraturan secara ascending
void selectionSort(string arr[], int n)
{
    for (int i = 0; i < n - 1; i++)
    {
        int minIndex = i;
        for (int j = i + 1; j < n; j++)
        {
            if (arr[j] < arr[minIndex])
            {
                minIndex = j;
            }
        }
        if (minIndex != i)
        {
            swap(arr[i], arr[minIndex]);
        }
    }
}

void tampilkanLangkahPembuatanAkun()
{
    cout << "------------------------------------------------\n";
    cout << "          LANGKAH PEMBUATAN AKUN \n";
    cout << "------------------------------------------------\n";
    cout << "Berikut langkah-langkah pembuatan akun\n";
    cout << "1. Isi formulir\n";
    cout << "2. Mengajukan formulir\n";
    cout << "3. Konfirmasi surat persetujuan\n";
}

void tampilkanIsiFormulir()
{
    string namalengkap, jeniskelamin, keperluan, kesehatan, pengalaman;
    cout << "------------------------------------------------\n";
    cout << "          FORMULIR PEMBUATAN AKUN \n";
    cout << "------------------------------------------------\n";
    cout << "Isi Nama Lengkap : ";
    cin.ignore();
    getline(cin, namalengkap);
    cout << "Pilih Jenis Kelamin (L/P) : ";
    cin.ignore();
    getline(cin, jeniskelamin);
    cout << "Keperluan : ";
    cin.ignore();
    getline(cin, keperluan);
    cout << "Pengalaman : ";
    cin.ignore();
    getline(cin, pengalaman);
    cout << "Catatan Kesehatan : ";
    cin.ignore();
    getline(cin, kesehatan);
}

void tampilkanInformasiAkun()
{
    cout << "Formulir telah disetujui oleh penanggung jawab  \n";
    cout << "------------------------------------------------\n";
    cout << "           I N F O R M A S I  A K U N           \n";
    cout << "------------------------------------------------\n";
    cout << "Username : user \n";
    cout << "Password : pass \n";
}

void isiMenuUtama()
{
    // Inisialisasi pencarian kontak
    const int banyak = 5;
    string nama[banyak] = {"Mark", "Renjana", "Jevano", "Haikal", "Nana"};
    string nomorTelepon[banyak] = {"081999080213", "082300200356", "083204000258", "082000606074", "081300028077"};
    string namaCari;

    // inisialisasi selection sort ascending
    const int jumlahAturan = 10;
    string aturan[jumlahAturan] = {
        "Pengguna laboratorium wajib menggunakan jas laboratorium serta Alat Pelindung Diri (APD) lengkap.",
        "Mengisi buku kunjungan laboratorium.",
        "Mengetahui fasilitas laboratorium, mengenal dan berkoordinasi dengan koordinator laboratorium.",
        "Menyimpan barang bawaan didalam loker yang telah disediakan.",
        "Tidak dibenarkan membawa makanan dan minuman, merokok dan berhias di dalam laboratorium.",
        "Pengguna laboratorium tidak diperbolehkan bercanda selama praktikum.",
        "Apabila mengalami kondisi yang tidak aman, kecelakaan atau kerusakan alat segera melapor kepada petugas laboratorium.",
        "Ikut menjaga dan merawat fasilitas laboratorium.",
        "Jika terjadi kebakaran, singkirkan atau jauhkan semua bahan atau barang dari api dan gunakan alat pemadam kebakaran yang tersedia.",
        "Mematuhi dan memenuhi standar kerja di laboratorium."};

    // inisialisasi jadwal
    const int jumlah = 5;
    Jadwal tanggal[jumlah] = {"  1 Februari 2024 ", "    3 Maret 2024  ", "   12 Maret 2024  ", " 15 Februari 2024 ", " 23 Januari 2024  "};
    Jadwal waktu[jumlah] = {" 07.00 - 10.00  ", " 18.00 - 21.00  ", " 06.00 - 09.00  ", " 09.00 - 12.00  ", " 13.00 - 16.00  "};
    Jadwal lokasi[jumlah] = {" Lab pr. kimia 1 ", " Lab pr. kimia 2 ", " Lab pr. kimia 1 ", " Lab pr. kimia 2 ", " Lab pr. kimia 1 "};
    Jadwal praktikum[jumlah] = {"  - ", " Penanganan bahaya kimia dalam pratikum ", "  -  ", " Resiko kesehatan penggunaan bahan kimia ", " Pengaruh paparan bahan kimia bagi kesehatan "};
    Jadwal penanggungJawab[jumlah] = {" Renjana ", " Haikal ", " Nana ", " Jevano ", " Mark "};
    Jadwal ketersediaan[jumlah] = {" Tersedia ", " Tidak ", " Tersedia ", " Tidak ", " Tidak "};
    string x;

    do
    {
        cout << "Masukkan pilihan (1 - 5): ";
        cin >> pilihan;

        switch (pilihan)
        {
        case 1:
            tampilkanPresensi();

            cout << endl;
            cout << "Menu Utama (0) : ";
            cin >> keluarmenuUtama;
            if (keluarmenuUtama == 0)
            {
                tampilkanMenuUtama();
                break;
            }
            break;

        case 2:
            tampilkanJadwalLaboratorium();
            // Input yang ingin dicari
            cout << "Masukkan yang ingin dicari: ";
            cin.ignore();
            getline (cin, x);
            
            int indeks = sequentialSearchJadwal(tanggal, jumlah, x);
            // Tampilkan hasil
            if (indeks != -1)
            {
                cout << "Jadwal '" << x << "' ditemukan pada urutan ke - " << indeks + 1 << " : "
                     << endl;
                cout << tanggal[indeks] << "  " << waktu[indeks] << "   " << lokasi[indeks] << "   " << praktikum[indeks] << "   " << penanggungJawab[indeks] << "    " << ketersediaan[indeks] << endl;
            }
            else
            {
                cout << "Jadwal '" << x << "' tidak ditemukan dalam array.";
            }
            cout << endl;
            cout << "Menu Utama (0) : ";
            cin >> keluarmenuUtama;
            if (keluarmenuUtama == 0)
            {
                tampilkanMenuUtama();
                break;
            }
            break;

        case 3:
            tampilkanNomorKontak();

            cout << endl;
            cout << "Huruf kapital digunakan pada huruf depan nama.\n";
            cout << "Masukkan nama yang ingin dicari: ";
            cin >> namaCari;

            indeks = sequentialSearch(nama, banyak, namaCari);

            if (indeks != -1)
            {
                cout << endl;
                cout << "Nomor telepon " << namaCari << ": " << nomorTelepon[indeks] << endl;
            }
            else
            {
                cout << endl;
                cout << "Kontak tidak ditemukan dalam daftar.\n";
            }
            cout << endl;
            cout << "Menu Utama (0) : ";
            cin >> keluarmenuUtama;
            if (keluarmenuUtama == 0)
            {
                tampilkanMenuUtama();
                break;
            }

            break;

        case 4:
            tampilkanPeraturanLaboratorium();

            selectionSort(aturan, jumlahAturan);

            cout << "\nBerikut merupakan peraturan yang wajib ditaati (A-Z) :" << endl;
            for (int i = 0; i < jumlahAturan; i++)
            {
                cout << i + 1 << ". " << aturan[i] << endl;
            }

            cout << "Menu Utama (0) : ";
            cin >> keluarmenuUtama;
            if (keluarmenuUtama == 0)
            {
                tampilkanMenuUtama();
                break;
            }
            break;
        case 5:
            cout << "Anda telah keluar dari program\n";
            cout << "-------- Terima Kasih --------\n";
            break;

        default:
            cout << "Pilihan Tidak Valid\n";
            break;
        }
        cout << endl;
    } while (pilihan != 5);
}

void IsiPembuatanAkun()
{
    do
    {
        cout << "Masukkan pilihan : ";
        cin >> pembuatanakun;

        switch (pembuatanakun)
        {
        case 1:
            tampilkanIsiFormulir();

            cout << "Menu Pembuatan Akun (0) : ";
            cin >> keluarmenuUtama;
            if (keluarmenuUtama == 0)
            {
                tampilkanLangkahPembuatanAkun();
            }
            break;

        case 2:
            tampilkanNomorKontak();

            cout << "Menu Pembuatan Akun (0) : ";
            cin >> keluarmenuUtama;
            if (keluarmenuUtama == 0)
            {
                tampilkanLangkahPembuatanAkun();
            }
            break;

        case 3:
            tampilkanInformasiAkun();

            cout << "0. Menu Pembuatan Akun\n";
            cout << "1. Menu Utama\n";
            cout << "Klik angka : ";
            cin >> keluarmenuUtama;
            if (keluarmenuUtama == 0)
            {
                tampilkanLangkahPembuatanAkun();
            }
            else
            {
                tampilkanMenuUtama();
                isiMenuUtama();
            }
            break;

        default:
            cout << "Pilihan tidak valid \n";
            break;
        }
    } while (pembuatanakun != 3);
}

int main()
{
    cout << "------------------------------------------------\n";
    cout << "   ~~~~~~ CHEMISTRY LABORATORIUM ACCESS ~~~~~~  \n";
    cout << "------------------------------------------------\n";

    // memastikan sudah memiliki akun
    cout << "Sudah memiliki akun? (Y / N): ";
    cin >> memilikiakun;
    cin.ignore();

    if (memilikiakun == 'Y' || memilikiakun == 'y')
    {

        do
        {
            cout << "Masukkan username: ";
            cin >> username;
            cout << "Masukkan password: ";
            cin >> password;

            // Cek login
            if (username == "user" && password == "pass")
            {
                cout << "\n=== Selamat datang di Laboratorium ===\n"
                     << endl;

                // Loop menu utama

                tampilkanMenuUtama();
                isiMenuUtama();
            }
            else
            {

                percobaanLogin--;
                if (percobaanLogin > 0)
                {
                    cout << "Username dan Password salah \n";
                    cout << "Sisa Kesempatan login : " << percobaanLogin << endl;
                    cout << "------------------------------------------------\n";
                }

                // tampilan apabila password dan username 3x salah
                else
                {
                    cout << "Anda telah 3x salah memasukkan password.\n";
                    cout << "------------------------------------------------\n";
                    cout << "  Silahkan tunggu beberapa saat. Terima kasih. \n\n";
                    break;
                }
            }
        } while (percobaanLogin > 0);
    }

    else
    {
        cout << "Silahkan lakukan pembuatan akun terlebih dahulu \n";
        cout << endl;

        tampilkanLangkahPembuatanAkun();
        IsiPembuatanAkun();
    }

    return 0;
}
