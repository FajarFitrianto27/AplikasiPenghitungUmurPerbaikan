# AplikasiPenghitungUmur(PERBAIKAN)
 Menambahkan Beberapa Variasi 

---

# **📌 Penghitung Umur**  
🕰️ **Penghitung Umur** adalah aplikasi sederhana berbasis **Java** menggunakan **NetBeans dan JDateChooser**, yang digunakan untuk menghitung **umur seseorang berdasarkan tanggal lahir yang dimasukkan**.  

Aplikasi ini juga bisa menghitung **berapa lama lagi menuju ulang tahun berikutnya** secara otomatis! 🎉  

---



---

## **🚀 Fitur Aplikasi**  
✅ **Menghitung umur berdasarkan tanggal lahir**  
✅ **Menampilkan umur dalam format (tahun, bulan, hari)**  
✅ **Menghitung berapa lama lagi menuju ulang tahun berikutnya**  
✅ **Perhitungan otomatis saat tanggal diubah di `JDateChooser`**  
✅ **Tombol "HITUNG" untuk perhitungan manual**  

---

## **🛠 Teknologi yang Digunakan**  
- **Java** (JDK 8 / 11 / 17)  
- **NetBeans IDE**  
- **JDateChooser (com.toedter.calendar)** untuk pemilihan tanggal  

---


---

## **📜 Cara Menggunakan**  
1️⃣ **Pilih tanggal lahir di `JDateChooser`**  
2️⃣ **Umur akan langsung dihitung secara otomatis**  
3️⃣ **Klik tombol "HITUNG" jika ingin menghitung manual**  
4️⃣ **Hasil umur akan muncul di `jTextField1`**  
5️⃣ **Jumlah bulan & hari menuju ulang tahun berikutnya muncul di `jTextField3`**  

---

## **📌 Kode Utama (PenghitungUmur.java)**
```java
import java.time.LocalDate;
import java.time.Period;
import java.time.ZoneId;
import java.util.Date;
import com.toedter.calendar.JDateChooser;

public class PenghitungUmur extends javax.swing.JFrame {

    public PenghitungUmur() {
        initComponents();
    }

   
    private void hitungUmurActionPerformed(java.awt.event.ActionEvent evt) {                                           
    Date tanggalLahir = jDateChooser1.getDate();
    if (tanggalLahir != null) {
        LocalDate lahir = tanggalLahir.toInstant().atZone(ZoneId.systemDefault()).toLocalDate();
        LocalDate sekarang = LocalDate.now();

        Period selisih = Period.between(lahir, sekarang);
        jTextField1.setText(selisih.getYears() + " Tahun " + selisih.getMonths() + " Bulan " + selisih.getDays() + " Hari");

        // Menghitung ulang tahun berikutnya
        LocalDate ulangTahunBerikutnya = lahir.withYear(sekarang.getYear());
        if (ulangTahunBerikutnya.isBefore(sekarang) || ulangTahunBerikutnya.equals(sekarang)) {
            ulangTahunBerikutnya = ulangTahunBerikutnya.plusYears(1);
        }
        Period sisaWaktu = Period.between(sekarang, ulangTahunBerikutnya);
        jTextField3.setText(sisaWaktu.getMonths() + " Bulan " + sisaWaktu.getDays() + " Hari");
    }
    }                                          

    private void jTextField2ActionPerformed(java.awt.event.ActionEvent evt) {                                            
        // TODO add your handling code here:
    }                                           

    private void jDateChooser1PropertyChange(java.beans.PropertyChangeEvent evt) {                                             
       if ("date".equals(evt.getPropertyName()) && jDateChooser1.getDate() != null) {
        hitungUmurActionPerformed(null); // Panggil langsung hitungUmurActionPerformed
    }
    }                                            

   
    public static void main(String args[]) {
       
        java.awt.EventQueue.invokeLater(new Runnable() {
            public void run() {
                new PenghitungUmur().setVisible(true);
            }
        });
    }

    // Variables declaration - do not modify                     
    private javax.swing.JButton hitungUmur;
    private com.toedter.calendar.JDateChooser jDateChooser1;
    private javax.swing.JLabel jLabel1;
    private javax.swing.JLabel jLabel2;
    private javax.swing.JLabel jLabel3;
    private javax.swing.JLabel jLabel4;
    private javax.swing.JTextField jTextField1;
    private javax.swing.JTextField jTextField2;
    private javax.swing.JTextField jTextField3;
    // End of variables declaration                   
}
```

---

 
```

---

## **📄 Lisensi**  


---

