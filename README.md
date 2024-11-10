
# Aplikasi Perhitungan Diskon
Tugas 3 - Muhammad Raihan Fadhillah 2210010404
## Deskripsi
Aplikasi Perhitungan Diskon adalah program berbasis Java yang dirancang untuk menghitung harga akhir setelah penerapan diskon. Aplikasi ini memiliki antarmuka pengguna grafis (GUI) yang intuitif, memungkinkan pengguna untuk memasukkan harga awal, memilih diskon, dan menerapkan kupon diskon. Hasil perhitungan akan ditampilkan secara langsung, dan riwayat diskon yang diterapkan akan disimpan dalam aplikasi.

## Daftar Isi
- [Deskripsi](#deskripsi)
- [Prerequisites](#prerequisites)
- [Fitur](#fitur)
- [Cara Menjalankan](#cara-menjalankan)
- [Dokumentasi](#dokumentasi)
- [Screenshots](#screenshots)
- [Contoh Penggunaan](#contoh-penggunaan)
- [Pembuat](#pembuat)

## Prerequisites
Sebelum menjalankan aplikasi ini, pastikan Anda telah menginstal:
- Java Development Kit (JDK) versi 8 atau yang lebih baru.
- IDE seperti IntelliJ IDEA, Eclipse, atau NetBeans untuk menjalankan dan mengembangkan aplikasi.

## Fitur   
1. Input harga awal dari pengguna.
2. Pilihan diskon melalui combo box.
3. Slider untuk memilih diskon secara visual.
4. Penerapan kupon diskon.
5. Menampilkan harga akhir dan jumlah yang dihemat.
6. Riwayat diskon yang diterapkan disimpan dan ditampilkan di area teks.


## Cara Menjalankan
1. Clone atau Download Repository:
    - Clone repository ini atau download sebagai ZIP dan ekstrak.

2. Buka Proyek di IDE:
    - Buka IDE Anda dan import proyek Java yang telah diunduh.

3. Jalankan Aplikasi:
    - Jalankan kelas AplikasiPerhitunganDiskon dari IDE Anda.
  
## Dokumentasi
- Method konstruktor
``` java
public AplikasiPerhitunganDiskon() {
        initComponents();
        
        sliderDiskon.addChangeListener(new ChangeListener() {
            public void stateChanged(ChangeEvent evt) {
                int sliderValue = sliderDiskon.getValue();
                comboDiskon.setSelectedItem(sliderValue + "%");
            }
        });

        // Add combo box listener
        comboDiskon.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String selectedItem = (String) comboDiskon.getSelectedItem();
                if (!selectedItem.equals("Pilih Diskon")) {
                    int discountValue = Integer.parseInt(selectedItem.replace("%", ""));
                    sliderDiskon.setValue(discountValue);
                }
            }
        });
        
    }
```

- Method hitung harga
``` java
private void btnHitungActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:
        try {
        int hargaAwal, hargaAkhir, hemat;
        String diskon = comboDiskon.getSelectedItem().toString();
        String kupon = "5persen";
        hargaAwal = Integer.parseInt(txtHargaAwal.getText()); // Mengubah input ke dalam integer

        // Apply coupon discount first if coupon is valid
        if (txtKupon.getText().equals(kupon)) {
            hargaAkhir = hargaAwal - (hargaAwal * 5 / 100);
        } else {
            hargaAkhir = hargaAwal; // Jika tidak ada kupon hargaAkhir disimpan sebagai hargaAwal
        }

        // Tambahkan diskon tambahan setelah adanya kupon
        switch (diskon) {
            case "10%":
                hargaAkhir -= (hargaAkhir * 10) / 100;
                break;
            case "20%":
                hargaAkhir -= (hargaAkhir * 20) / 100;
                break;
            case "30%":
                hargaAkhir -= (hargaAkhir * 30) / 100;
                break;
            case "40%":
                hargaAkhir -= (hargaAkhir * 40) / 100;
                break;
            case "50%":
                hargaAkhir -= (hargaAkhir * 50) / 100;
                break;
            case "60%":
                hargaAkhir -= (hargaAkhir * 60) / 100;
                break;
            case "70%":
                hargaAkhir -= (hargaAkhir * 70) / 100;
                break;
        }

        // Hitung hemat dari harga awal
        hemat = hargaAwal - hargaAkhir;

        // Menampilkan hasil
        txtHargaAkhir.setText(String.valueOf(hargaAkhir));
        txtHemat.setText(String.valueOf(hemat));

        // Menambahkan history
        String history = "Harga Awal: " + hargaAwal + ", Diskon: " + diskon 
                         + ", Kupon: " + (txtKupon.getText().equals(kupon) ? "5%" : "None") 
                         + ", Harga Akhir: " + hargaAkhir + ", Hemat: " + hemat + "\n";
        areaRiwayat.append(history);

        } catch (NumberFormatException e) {
            // Validasi input
            javax.swing.JOptionPane.showMessageDialog(this, "Masukkan hanya angka untuk harga awal.", 
                    "Input Tidak Valid", javax.swing.JOptionPane.ERROR_MESSAGE);
        }

    }   
```

## Screenshots

![Screenshot 2024-11-10 173014](https://github.com/user-attachments/assets/0e1341a2-869a-45c4-974d-9e83382955c4)



## Contoh Penggunaan
1. Masukkan harga awal di kolom "Harga Awal".
2. Pilih diskon dari combo box (misalnya, "20%").
3. Masukkan kupon diskon jika ada (contoh: "5persen").
4. Klik tombol "Hitung" untuk menghitung harga akhir.
5. Hasil perhitungan akan ditampilkan di kolom "Harga Akhir" dan "Anda Hemat".
5. Riwayat diskon yang diterapkan akan ditampilkan di area "Riwayat Diskon".



## Pembuat

- Nama : Muhammad Raihan Fadhillah
- NPM : 2210010404

