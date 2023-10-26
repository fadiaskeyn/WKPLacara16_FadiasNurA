/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package Admin;

import java.awt.Color;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.sql.Connection;
import java.sql.Statement;
import java.util.Random;
import javax.swing.JOptionPane;
import javax.swing.Timer;
import javax.swing.table.DefaultTableCellRenderer;
import javax.swing.table.DefaultTableModel;

/**
 *
 * @author pc
 */
public class DashboardAdmin extends javax.swing.JFrame {

    /**
     * Creates new form DashboardAdmin
     */
    
    public Color clicked,normal;
    
    public DashboardAdmin() {
        initComponents();
        setLocationRelativeTo(this);
        tampil_table_obat();
        tampil_tableDokter();
        
        colorku();
        halaman();
        
        Dashboard.setVisible(true);
        btn_dashboard.setBackground(clicked);
    }
    
    private boolean perizinanAkses() {
        String sts = status.getText();
        return sts.equals("admin");
    }
    
    public void colorku(){
        clicked = new Color(0,63,121);
        normal  = new Color(0,45,89);
        btn_dashboard.setBackground(normal);
        btn_dokter.setBackground(normal);
        btn_laporan.setBackground(normal);
        btn_resep.setBackground(normal);
        btn_obat.setBackground(normal);
        refresh_inputDokter();
        refresh_inputObat();
        IDdokter();
        KDobat();
    }
    
    void refresh_inputObat(){
        txt_kodeobat.setText("");
        txt_namaobat.setText("");
        txt_hargaobat.setText("");
        txt_jenisobat.setText("");
        txt_stokobat.setText("");
    }
    
    void refresh_inputDokter(){
        txt_iddokter.setText("");
        txt_namadokter.setText("");
        txt_spesialisdokter.setText("");
        txt_telpdokter.setText("");
    }

    private void halaman(){
        Obat.setVisible(false);
        DetailObat.setVisible(false);
        TambahObat.setVisible(false);
        Resep.setVisible(false);
        Dokter.setVisible(false);
        TambahDokter.setVisible(false);
        DetailDokter.setVisible(false);
        Laporan.setVisible(false);
    }
    
    private static int generateRandomCode() {
        Random random = new Random();
        int randomNumber = random.nextInt(9000) + 1000; 
        return randomNumber;
    }
    
    public void KDobat() {
        int randomNumber = generateRandomCode();
        String kdobat = "P" + String.valueOf(randomNumber);
        txt_kodeobat.setText(kdobat);
    }
    
    public void IDdokter(){
        int randomNumber = generateRandomCode();
        String iddokter = "D" + generateRandomCode();
        txt_iddokter.setText(iddokter);
    }
    
    public void tampil_table_obat(){
        DefaultTableModel model=new DefaultTableModel();
        model.addColumn("Kode Obat");
        model.addColumn("Nama Obat");
        model.addColumn("Harga Obat");
        model.addColumn("Stok Obat");
        model.addColumn("Stok Obat");
        
        try {
            int no=1;
            String sql = "SELECT * FROM obat ";
            java.sql.Connection conn=(Connection)Config.koneksi.configDBek();
            java.sql.Statement stm=conn.createStatement();
            java.sql.ResultSet res=stm.executeQuery(sql);
            while(res.next()){
                model.addRow(new Object[]{res.getString(1),res.getString(2),
                        res.getString(3),res.getString(4),res.getString(5)
                        });
        }
            tabel_obat.setModel(model);
        } catch (Exception e) {
            System.out.println("gagal tampil tabel obat "+e.getMessage());
        }
    }
    
       public void resep(){
        DefaultTableModel model=new DefaultTableModel();
        model.addColumn("Kode Obat");
        model.addColumn("Nama Obat");
        model.addColumn("Harga Obat");
        model.addColumn("Stok Obat");
        model.addColumn("Stok Obat");
        
        try {
            int no=1;
            String sql = "SELECT * FROM obat ";
            java.sql.Connection conn=(Connection)Config.koneksi.configDBek();
            java.sql.Statement stm=conn.createStatement();
            java.sql.ResultSet res=stm.executeQuery(sql);
            while(res.next()){
                model.addRow(new Object[]{res.getString(1),res.getString(2),
                        res.getString(3),res.getString(4),res.getString(5)
                        });
        }
            tabel_obat.setModel(model);
        } catch (Exception e) {
            System.out.println("gagal tampil tabel obat "+e.getMessage());
        }
    }
    
    public void tampil_tableDokter(){
        DefaultTableModel model=new DefaultTableModel();
        model.addColumn("ID Dokter");
        model.addColumn("Nama Lengkap");
        model.addColumn("Spesialis");
        model.addColumn("Telepon");
        
        try {
            int no=1;
            String sql = "SELECT * FROM dokter ";
            java.sql.Connection conn=(Connection)Config.koneksi.configDBek();
            java.sql.Statement stm=conn.createStatement();
            java.sql.ResultSet res=stm.executeQuery(sql);
            while(res.next()){
                model.addRow(new Object[]{res.getString(1),res.getString(2),
                        res.getString(3),res.getString(4)
                        });
        }
            tabel_dokter.setModel(model);
        } catch (Exception e) {
            System.out.println("gagal tampil tabel obat "+e.getMessage());
        }
    }

    /**
     * This method is called from within the constructor to initialize the form.
     * WARNING: Do NOT modify this code. The content of this method is always
     * regenerated by the Form Editor.
     */
    @SuppressWarnings("unchecked")
    // <editor-fold defaultstate="collapsed" desc="Generated Code">                          
    private void initComponents() {

        btn_keluar = new Swing.btnroundkotakcb();
        btn_dashboard = new Swing.btnroundkotakcb();
        btn_obat = new Swing.btnroundkotakcb();
        btn_resep = new Swing.btnroundkotakcb();
        btn_dokter = new Swing.btnroundkotakcb();
        btn_laporan = new Swing.btnroundkotakcb();
        status = new javax.swing.JTextField();
        Dashboard = new javax.swing.JPanel();
        Teks = new javax.swing.JTextField();
        jLabel3 = new javax.swing.JLabel();
        Obat = new javax.swing.JPanel();
        btntambah_obat = new Swing.btnroundkotak();
        jScrollPane1 = new javax.swing.JScrollPane();
        tabel_obat = new javax.swing.JTable();
        jLabel4 = new javax.swing.JLabel();
        TambahObat = new javax.swing.JPanel();
        txt_kodeobat = new javax.swing.JTextField();
        txt_namaobat = new javax.swing.JTextField();
        txt_hargaobat = new javax.swing.JTextField();
        txt_jenisobat = new javax.swing.JTextField();
        txt_stokobat = new javax.swing.JTextField();
        btn_simpanobat = new Swing.btnroundkotak();
        jLabel9 = new javax.swing.JLabel();
        DetailObat = new javax.swing.JPanel();
        kodeobat = new javax.swing.JTextField();
        namaobat = new javax.swing.JTextField();
        hargaobat = new javax.swing.JTextField();
        jenisobat = new javax.swing.JTextField();
        stokobat = new javax.swing.JTextField();
        btn_hapusobat = new Swing.btnroundkotak();
        btn_ubahobat = new Swing.btnroundkotak();
        jLabel8 = new javax.swing.JLabel();
        Resep = new javax.swing.JPanel();
        jLabel5 = new javax.swing.JLabel();
        Dokter = new javax.swing.JPanel();
        btn_tambahdokter = new Swing.btnroundkotak();
        jScrollPane2 = new javax.swing.JScrollPane();
        tabel_dokter = new javax.swing.JTable();
        Jpanel111 = new javax.swing.JLabel();
        TambahDokter = new javax.swing.JPanel();
        txt_iddokter = new javax.swing.JTextField();
        txt_namadokter = new javax.swing.JTextField();
        txt_spesialisdokter = new javax.swing.JTextField();
        txt_telpdokter = new javax.swing.JTextField();
        btn_simpandokter = new Swing.btnroundkotak();
        jLabel10 = new javax.swing.JLabel();
        DetailDokter = new javax.swing.JPanel();
        iddokter = new javax.swing.JTextField();
        namadokter = new javax.swing.JTextField();
        spesialisdokter = new javax.swing.JTextField();
        telpdokter = new javax.swing.JTextField();
        btn_hapusdokter = new Swing.btnroundkotak();
        btn_ubahdokter = new Swing.btnroundkotak();
        jLabel11 = new javax.swing.JLabel();
        Laporan = new javax.swing.JPanel();
        jLabel7 = new javax.swing.JLabel();
        BG = new javax.swing.JLabel();
        namauser = new javax.swing.JTextField();

        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);
        setUndecorated(true);
        getContentPane().setLayout(new org.netbeans.lib.awtextra.AbsoluteLayout());

        btn_keluar.setBackground(new java.awt.Color(0, 105, 182));
        btn_keluar.setForeground(new java.awt.Color(204, 204, 204));
        btn_keluar.setIcon(new javax.swing.ImageIcon(getClass().getResource("/img/icon-keluar.png"))); // NOI18N
        btn_keluar.setActionCommand("Obat");
        btn_keluar.setFont(new java.awt.Font("Montserrat Black", 0, 24)); // NOI18N
        btn_keluar.setHorizontalAlignment(javax.swing.SwingConstants.LEFT);
        btn_keluar.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btn_keluarActionPerformed(evt);
            }
        });
        getContentPane().add(btn_keluar, new org.netbeans.lib.awtextra.AbsoluteConstraints(16, 650, 310, 70));

        btn_dashboard.setBackground(new java.awt.Color(0, 45, 89));
        btn_dashboard.setForeground(new java.awt.Color(204, 204, 204));
        btn_dashboard.setIcon(new javax.swing.ImageIcon(getClass().getResource("/img/icon-dashboard.png"))); // NOI18N
        btn_dashboard.setFont(new java.awt.Font("Montserrat Black", 0, 24)); // NOI18N
        btn_dashboard.setHorizontalAlignment(javax.swing.SwingConstants.LEFT);
        btn_dashboard.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btn_dashboardActionPerformed(evt);
            }
        });
        getContentPane().add(btn_dashboard, new org.netbeans.lib.awtextra.AbsoluteConstraints(16, 151, 310, 70));

        btn_obat.setBackground(new java.awt.Color(0, 46, 89));
        btn_obat.setForeground(new java.awt.Color(204, 204, 204));
        btn_obat.setIcon(new javax.swing.ImageIcon(getClass().getResource("/img/icon-obat.png"))); // NOI18N
        btn_obat.setFont(new java.awt.Font("Montserrat Black", 0, 24)); // NOI18N
        btn_obat.setHorizontalAlignment(javax.swing.SwingConstants.LEFT);
        btn_obat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btn_obatActionPerformed(evt);
            }
        });
        getContentPane().add(btn_obat, new org.netbeans.lib.awtextra.AbsoluteConstraints(16, 221, 310, 70));

        btn_resep.setBackground(new java.awt.Color(0, 46, 89));
        btn_resep.setForeground(new java.awt.Color(204, 204, 204));
        btn_resep.setIcon(new javax.swing.ImageIcon(getClass().getResource("/img/icon-resep.png"))); // NOI18N
        btn_resep.setActionCommand("Obat");
        btn_resep.setFont(new java.awt.Font("Montserrat Black", 0, 24)); // NOI18N
        btn_resep.setHorizontalAlignment(javax.swing.SwingConstants.LEFT);
        btn_resep.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btn_resepActionPerformed(evt);
            }
        });
        getContentPane().add(btn_resep, new org.netbeans.lib.awtextra.AbsoluteConstraints(16, 361, 310, 70));

        btn_dokter.setBackground(new java.awt.Color(0, 46, 89));
        btn_dokter.setForeground(new java.awt.Color(204, 204, 204));
        btn_dokter.setIcon(new javax.swing.ImageIcon(getClass().getResource("/img/icon-dokter.png"))); // NOI18N
        btn_dokter.setActionCommand("Obat");
        btn_dokter.setFont(new java.awt.Font("Montserrat Black", 0, 24)); // NOI18N
        btn_dokter.setHorizontalAlignment(javax.swing.SwingConstants.LEFT);
        btn_dokter.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btn_dokterActionPerformed(evt);
            }
        });
        getContentPane().add(btn_dokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(16, 291, 310, 70));

        btn_laporan.setBackground(new java.awt.Color(0, 46, 89));
        btn_laporan.setForeground(new java.awt.Color(204, 204, 204));
        btn_laporan.setIcon(new javax.swing.ImageIcon(getClass().getResource("/img/icon-laporan.png"))); // NOI18N
        btn_laporan.setActionCommand("Obat");
        btn_laporan.setFont(new java.awt.Font("Montserrat Black", 0, 24)); // NOI18N
        btn_laporan.setHorizontalAlignment(javax.swing.SwingConstants.LEFT);
        btn_laporan.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btn_laporanActionPerformed(evt);
            }
        });
        getContentPane().add(btn_laporan, new org.netbeans.lib.awtextra.AbsoluteConstraints(16, 431, 310, 70));

        status.setEditable(false);
        status.setBackground(new java.awt.Color(215, 215, 215));
        status.setFont(new java.awt.Font("Montserrat", 1, 18)); // NOI18N
        status.setHorizontalAlignment(javax.swing.JTextField.RIGHT);
        status.setText("admin");
        status.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        getContentPane().add(status, new org.netbeans.lib.awtextra.AbsoluteConstraints(920, 14, 360, 40));

        Dashboard.setBackground(new java.awt.Color(255, 255, 255));
        Dashboard.setLayout(new org.netbeans.lib.awtextra.AbsoluteLayout());

        Teks.setEditable(false);
        Teks.setBackground(new java.awt.Color(255, 255, 255));
        Teks.setFont(new java.awt.Font("Montserrat", 1, 36)); // NOI18N
        Teks.setText("Selamat Datang");
        Teks.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        Dashboard.add(Teks, new org.netbeans.lib.awtextra.AbsoluteConstraints(20, 0, 770, 70));

        jLabel3.setBackground(new java.awt.Color(255, 255, 255));
        jLabel3.setFont(new java.awt.Font("Montserrat", 1, 36)); // NOI18N
        jLabel3.setForeground(new java.awt.Color(204, 204, 204));
        jLabel3.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel3.setText("DASHBOARD");
        Dashboard.add(jLabel3, new org.netbeans.lib.awtextra.AbsoluteConstraints(0, 0, 1020, 690));

        getContentPane().add(Dashboard, new org.netbeans.lib.awtextra.AbsoluteConstraints(346, 78, 1020, 690));

        Obat.setBackground(new java.awt.Color(255, 255, 255));
        Obat.setLayout(new org.netbeans.lib.awtextra.AbsoluteLayout());

        btntambah_obat.setBackground(new java.awt.Color(3, 93, 145));
        btntambah_obat.setForeground(new java.awt.Color(255, 255, 255));
        btntambah_obat.setText("Tambah");
        btntambah_obat.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        btntambah_obat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btntambah_obatActionPerformed(evt);
            }
        });
        Obat.add(btntambah_obat, new org.netbeans.lib.awtextra.AbsoluteConstraints(20, 50, 150, 50));

        tabel_obat.setFont(new java.awt.Font("Century Gothic", 0, 14)); // NOI18N
        tabel_obat.setModel(new javax.swing.table.DefaultTableModel(
            new Object [][] {

            },
            new String [] {
                "Title 1", "Title 2", "Title 3", "Title 4"
            }
        ));
        tabel_obat.addMouseListener(new java.awt.event.MouseAdapter() {
            public void mouseClicked(java.awt.event.MouseEvent evt) {
                tabel_obatMouseClicked(evt);
            }
        });
        jScrollPane1.setViewportView(tabel_obat);

        Obat.add(jScrollPane1, new org.netbeans.lib.awtextra.AbsoluteConstraints(20, 117, 980, 530));

        jLabel4.setBackground(new java.awt.Color(255, 255, 255));
        jLabel4.setFont(new java.awt.Font("Montserrat", 1, 36)); // NOI18N
        jLabel4.setForeground(new java.awt.Color(204, 204, 204));
        jLabel4.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel4.setText("OBAT");
        Obat.add(jLabel4, new org.netbeans.lib.awtextra.AbsoluteConstraints(0, 0, 1050, 690));

        getContentPane().add(Obat, new org.netbeans.lib.awtextra.AbsoluteConstraints(346, 78, 1020, 690));

        TambahObat.setBackground(new java.awt.Color(255, 255, 255));
        TambahObat.setLayout(new org.netbeans.lib.awtextra.AbsoluteLayout());

        txt_kodeobat.setEditable(false);
        txt_kodeobat.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        txt_kodeobat.setForeground(new java.awt.Color(64, 64, 64));
        txt_kodeobat.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        txt_kodeobat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                txt_kodeobatActionPerformed(evt);
            }
        });
        TambahObat.add(txt_kodeobat, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 211, 430, 30));

        txt_namaobat.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        txt_namaobat.setForeground(new java.awt.Color(64, 64, 64));
        txt_namaobat.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        txt_namaobat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                txt_namaobatActionPerformed(evt);
            }
        });
        TambahObat.add(txt_namaobat, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 265, 430, 30));

        txt_hargaobat.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        txt_hargaobat.setForeground(new java.awt.Color(64, 64, 64));
        txt_hargaobat.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        txt_hargaobat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                txt_hargaobatActionPerformed(evt);
            }
        });
        TambahObat.add(txt_hargaobat, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 317, 430, 30));

        txt_jenisobat.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        txt_jenisobat.setForeground(new java.awt.Color(64, 64, 64));
        txt_jenisobat.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        txt_jenisobat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                txt_jenisobatActionPerformed(evt);
            }
        });
        TambahObat.add(txt_jenisobat, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 373, 430, 30));

        txt_stokobat.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        txt_stokobat.setForeground(new java.awt.Color(64, 64, 64));
        txt_stokobat.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        txt_stokobat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                txt_stokobatActionPerformed(evt);
            }
        });
        TambahObat.add(txt_stokobat, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 428, 430, 30));

        btn_simpanobat.setBackground(new java.awt.Color(3, 93, 145));
        btn_simpanobat.setForeground(new java.awt.Color(255, 255, 255));
        btn_simpanobat.setFont(new java.awt.Font("Montserrat Medium", 1, 18)); // NOI18N
        btn_simpanobat.setLabel("Simpan");
        btn_simpanobat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btn_simpanobatActionPerformed(evt);
            }
        });
        TambahObat.add(btn_simpanobat, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 500, 100, 40));

        jLabel9.setBackground(new java.awt.Color(255, 255, 255));
        jLabel9.setFont(new java.awt.Font("Montserrat", 1, 36)); // NOI18N
        jLabel9.setForeground(new java.awt.Color(204, 204, 204));
        jLabel9.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel9.setIcon(new javax.swing.ImageIcon(getClass().getResource("/img/tambahobat.jpg"))); // NOI18N
        TambahObat.add(jLabel9, new org.netbeans.lib.awtextra.AbsoluteConstraints(0, 0, 1050, 690));

        getContentPane().add(TambahObat, new org.netbeans.lib.awtextra.AbsoluteConstraints(346, 78, 1020, 690));

        DetailObat.setBackground(new java.awt.Color(255, 255, 255));
        DetailObat.setLayout(new org.netbeans.lib.awtextra.AbsoluteLayout());

        kodeobat.setEditable(false);
        kodeobat.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        kodeobat.setForeground(new java.awt.Color(64, 64, 64));
        kodeobat.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        kodeobat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                kodeobatActionPerformed(evt);
            }
        });
        DetailObat.add(kodeobat, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 211, 430, 30));

        namaobat.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        namaobat.setForeground(new java.awt.Color(64, 64, 64));
        namaobat.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        namaobat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                namaobatActionPerformed(evt);
            }
        });
        DetailObat.add(namaobat, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 265, 430, 30));

        hargaobat.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        hargaobat.setForeground(new java.awt.Color(64, 64, 64));
        hargaobat.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        hargaobat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                hargaobatActionPerformed(evt);
            }
        });
        DetailObat.add(hargaobat, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 317, 430, 30));

        jenisobat.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        jenisobat.setForeground(new java.awt.Color(64, 64, 64));
        jenisobat.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        jenisobat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                jenisobatActionPerformed(evt);
            }
        });
        DetailObat.add(jenisobat, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 373, 430, 30));

        stokobat.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        stokobat.setForeground(new java.awt.Color(64, 64, 64));
        stokobat.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        stokobat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                stokobatActionPerformed(evt);
            }
        });
        DetailObat.add(stokobat, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 428, 430, 30));

        btn_hapusobat.setBackground(new java.awt.Color(225, 50, 50));
        btn_hapusobat.setForeground(new java.awt.Color(255, 255, 255));
        btn_hapusobat.setText("Hapus");
        btn_hapusobat.setFont(new java.awt.Font("Montserrat Medium", 1, 18)); // NOI18N
        btn_hapusobat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btn_hapusobatActionPerformed(evt);
            }
        });
        DetailObat.add(btn_hapusobat, new org.netbeans.lib.awtextra.AbsoluteConstraints(540, 500, 100, 40));

        btn_ubahobat.setBackground(new java.awt.Color(3, 93, 145));
        btn_ubahobat.setForeground(new java.awt.Color(255, 255, 255));
        btn_ubahobat.setText("Ubah");
        btn_ubahobat.setFont(new java.awt.Font("Montserrat Medium", 1, 18)); // NOI18N
        btn_ubahobat.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btn_ubahobatActionPerformed(evt);
            }
        });
        DetailObat.add(btn_ubahobat, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 500, 100, 40));

        jLabel8.setBackground(new java.awt.Color(255, 255, 255));
        jLabel8.setFont(new java.awt.Font("Montserrat", 1, 36)); // NOI18N
        jLabel8.setForeground(new java.awt.Color(204, 204, 204));
        jLabel8.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel8.setIcon(new javax.swing.ImageIcon(getClass().getResource("/img/detailobat.jpg"))); // NOI18N
        DetailObat.add(jLabel8, new org.netbeans.lib.awtextra.AbsoluteConstraints(0, 0, 1050, 690));

        getContentPane().add(DetailObat, new org.netbeans.lib.awtextra.AbsoluteConstraints(346, 78, 1020, 690));

        Resep.setBackground(new java.awt.Color(255, 255, 255));
        Resep.setLayout(new org.netbeans.lib.awtextra.AbsoluteLayout());

        jLabel5.setBackground(new java.awt.Color(255, 255, 255));
        jLabel5.setFont(new java.awt.Font("Montserrat", 1, 36)); // NOI18N
        jLabel5.setForeground(new java.awt.Color(204, 204, 204));
        jLabel5.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel5.setText("RESEP");
        Resep.add(jLabel5, new org.netbeans.lib.awtextra.AbsoluteConstraints(0, 0, 1050, 690));

        getContentPane().add(Resep, new org.netbeans.lib.awtextra.AbsoluteConstraints(346, 78, 1020, 690));

        Dokter.setBackground(new java.awt.Color(255, 255, 255));
        Dokter.setLayout(new org.netbeans.lib.awtextra.AbsoluteLayout());

        btn_tambahdokter.setBackground(new java.awt.Color(3, 93, 145));
        btn_tambahdokter.setForeground(new java.awt.Color(255, 255, 255));
        btn_tambahdokter.setText("Tambah");
        btn_tambahdokter.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        btn_tambahdokter.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btn_tambahdokterActionPerformed(evt);
            }
        });
        Dokter.add(btn_tambahdokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(20, 50, 150, 50));

        tabel_dokter.setFont(new java.awt.Font("Century Gothic", 0, 14)); // NOI18N
        tabel_dokter.setModel(new javax.swing.table.DefaultTableModel(
            new Object [][] {

            },
            new String [] {
                "Title 1", "Title 2", "Title 3", "Title 4"
            }
        ));
        tabel_dokter.addMouseListener(new java.awt.event.MouseAdapter() {
            public void mouseClicked(java.awt.event.MouseEvent evt) {
                tabel_dokterMouseClicked(evt);
            }
        });
        jScrollPane2.setViewportView(tabel_dokter);

        Dokter.add(jScrollPane2, new org.netbeans.lib.awtextra.AbsoluteConstraints(20, 117, 980, 530));

        Jpanel111.setBackground(new java.awt.Color(255, 255, 255));
        Jpanel111.setFont(new java.awt.Font("Montserrat", 1, 36)); // NOI18N
        Jpanel111.setForeground(new java.awt.Color(204, 204, 204));
        Jpanel111.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        Dokter.add(Jpanel111, new org.netbeans.lib.awtextra.AbsoluteConstraints(0, 0, 1050, 690));

        getContentPane().add(Dokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(346, 78, 1020, 690));

        TambahDokter.setBackground(new java.awt.Color(255, 255, 255));
        TambahDokter.setLayout(new org.netbeans.lib.awtextra.AbsoluteLayout());

        txt_iddokter.setEditable(false);
        txt_iddokter.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        txt_iddokter.setForeground(new java.awt.Color(64, 64, 64));
        txt_iddokter.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        txt_iddokter.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                txt_iddokterActionPerformed(evt);
            }
        });
        TambahDokter.add(txt_iddokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 211, 430, 30));

        txt_namadokter.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        txt_namadokter.setForeground(new java.awt.Color(64, 64, 64));
        txt_namadokter.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        txt_namadokter.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                txt_namadokterActionPerformed(evt);
            }
        });
        TambahDokter.add(txt_namadokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 265, 430, 30));

        txt_spesialisdokter.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        txt_spesialisdokter.setForeground(new java.awt.Color(64, 64, 64));
        txt_spesialisdokter.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        txt_spesialisdokter.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                txt_spesialisdokterActionPerformed(evt);
            }
        });
        TambahDokter.add(txt_spesialisdokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 317, 430, 30));

        txt_telpdokter.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        txt_telpdokter.setForeground(new java.awt.Color(64, 64, 64));
        txt_telpdokter.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        txt_telpdokter.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                txt_telpdokterActionPerformed(evt);
            }
        });
        TambahDokter.add(txt_telpdokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 373, 430, 30));

        btn_simpandokter.setBackground(new java.awt.Color(3, 93, 145));
        btn_simpandokter.setForeground(new java.awt.Color(255, 255, 255));
        btn_simpandokter.setFont(new java.awt.Font("Montserrat Medium", 1, 18)); // NOI18N
        btn_simpandokter.setLabel("Simpan");
        btn_simpandokter.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btn_simpandokterActionPerformed(evt);
            }
        });
        TambahDokter.add(btn_simpandokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 500, 100, 40));

        jLabel10.setBackground(new java.awt.Color(255, 255, 255));
        jLabel10.setFont(new java.awt.Font("Montserrat", 1, 36)); // NOI18N
        jLabel10.setForeground(new java.awt.Color(204, 204, 204));
        jLabel10.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel10.setIcon(new javax.swing.ImageIcon(getClass().getResource("/img/tambahdokter.jpg"))); // NOI18N
        TambahDokter.add(jLabel10, new org.netbeans.lib.awtextra.AbsoluteConstraints(0, 0, 1050, 690));

        getContentPane().add(TambahDokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(346, 78, 1020, 690));

        DetailDokter.setBackground(new java.awt.Color(255, 255, 255));
        DetailDokter.setLayout(new org.netbeans.lib.awtextra.AbsoluteLayout());

        iddokter.setEditable(false);
        iddokter.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        iddokter.setForeground(new java.awt.Color(64, 64, 64));
        iddokter.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        iddokter.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                iddokterActionPerformed(evt);
            }
        });
        DetailDokter.add(iddokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 211, 430, 30));

        namadokter.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        namadokter.setForeground(new java.awt.Color(64, 64, 64));
        namadokter.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        namadokter.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                namadokterActionPerformed(evt);
            }
        });
        DetailDokter.add(namadokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 265, 430, 30));

        spesialisdokter.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        spesialisdokter.setForeground(new java.awt.Color(64, 64, 64));
        spesialisdokter.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        spesialisdokter.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                spesialisdokterActionPerformed(evt);
            }
        });
        DetailDokter.add(spesialisdokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 317, 430, 30));

        telpdokter.setFont(new java.awt.Font("Century Gothic", 1, 24)); // NOI18N
        telpdokter.setForeground(new java.awt.Color(64, 64, 64));
        telpdokter.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        telpdokter.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                telpdokterActionPerformed(evt);
            }
        });
        DetailDokter.add(telpdokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 373, 430, 30));

        btn_hapusdokter.setBackground(new java.awt.Color(225, 50, 50));
        btn_hapusdokter.setForeground(new java.awt.Color(255, 255, 255));
        btn_hapusdokter.setText("Hapus");
        btn_hapusdokter.setFont(new java.awt.Font("Montserrat Medium", 1, 18)); // NOI18N
        btn_hapusdokter.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btn_hapusdokterActionPerformed(evt);
            }
        });
        DetailDokter.add(btn_hapusdokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(540, 500, 100, 40));

        btn_ubahdokter.setBackground(new java.awt.Color(3, 93, 145));
        btn_ubahdokter.setForeground(new java.awt.Color(255, 255, 255));
        btn_ubahdokter.setText("Ubah");
        btn_ubahdokter.setFont(new java.awt.Font("Montserrat Medium", 1, 18)); // NOI18N
        btn_ubahdokter.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btn_ubahdokterActionPerformed(evt);
            }
        });
        DetailDokter.add(btn_ubahdokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(420, 500, 100, 40));

        jLabel11.setBackground(new java.awt.Color(255, 255, 255));
        jLabel11.setFont(new java.awt.Font("Montserrat", 1, 36)); // NOI18N
        jLabel11.setForeground(new java.awt.Color(204, 204, 204));
        jLabel11.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel11.setIcon(new javax.swing.ImageIcon(getClass().getResource("/img/detaildokter.jpg"))); // NOI18N
        DetailDokter.add(jLabel11, new org.netbeans.lib.awtextra.AbsoluteConstraints(0, 0, 1050, 690));

        getContentPane().add(DetailDokter, new org.netbeans.lib.awtextra.AbsoluteConstraints(346, 78, 1020, 690));

        Laporan.setBackground(new java.awt.Color(255, 255, 255));
        Laporan.setLayout(new org.netbeans.lib.awtextra.AbsoluteLayout());

        jLabel7.setBackground(new java.awt.Color(255, 255, 255));
        jLabel7.setFont(new java.awt.Font("Montserrat", 1, 36)); // NOI18N
        jLabel7.setForeground(new java.awt.Color(204, 204, 204));
        jLabel7.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel7.setText("LAPORAN");
        Laporan.add(jLabel7, new org.netbeans.lib.awtextra.AbsoluteConstraints(0, 0, 1050, 690));

        getContentPane().add(Laporan, new org.netbeans.lib.awtextra.AbsoluteConstraints(346, 78, 1020, 690));

        BG.setIcon(new javax.swing.ImageIcon(getClass().getResource("/img/bg-dashboard.jpg"))); // NOI18N
        getContentPane().add(BG, new org.netbeans.lib.awtextra.AbsoluteConstraints(0, 0, 1366, 768));

        namauser.setEditable(false);
        namauser.setBackground(new java.awt.Color(215, 215, 215));
        namauser.setFont(new java.awt.Font("Montserrat", 1, 24)); // NOI18N
        namauser.setHorizontalAlignment(javax.swing.JTextField.RIGHT);
        namauser.setBorder(javax.swing.BorderFactory.createEmptyBorder(1, 1, 1, 1));
        getContentPane().add(namauser, new org.netbeans.lib.awtextra.AbsoluteConstraints(450, 14, 360, 40));

        pack();
    }// </editor-fold>                        

    private void btn_dashboardActionPerformed(java.awt.event.ActionEvent evt) {                                              
        // TODO add your handling code here:
        Dashboard.setVisible(true);
        colorku();
        btn_dashboard.setBackground(clicked);
        Obat.setVisible(false);
        DetailObat.setVisible(false);
        TambahObat.setVisible(false);
        Resep.setVisible(false);
        Dokter.setVisible(false);
        TambahDokter.setVisible(false);
        DetailDokter.setVisible(false);
        Laporan.setVisible(false);
    }                                             

    private void btn_resepActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:
        Dashboard.setVisible(false);
        Obat.setVisible(false);
        DetailObat.setVisible(false);
        TambahObat.setVisible(false);
        Resep.setVisible(true);
        colorku();
        btn_resep.setBackground(clicked);
        Dokter.setVisible(false);
        TambahDokter.setVisible(false);
        DetailDokter.setVisible(false);
        Laporan.setVisible(false);
    }                                         

    private void btn_dokterActionPerformed(java.awt.event.ActionEvent evt) {                                           
        // TODO add your handling code here:
        Dashboard.setVisible(false);
        Obat.setVisible(false);
        DetailObat.setVisible(false);
        TambahObat.setVisible(false);
        Resep.setVisible(false);
        Dokter.setVisible(true);
        TambahDokter.setVisible(false);
        DetailDokter.setVisible(false);
        colorku();
        btn_dokter.setBackground(clicked);
        Laporan.setVisible(false);
    }                                          

    private void btn_laporanActionPerformed(java.awt.event.ActionEvent evt) {                                            
        // TODO add your handling code here:
        if (perizinanAkses()) { 
        // Tambahkan kode Anda untuk beralih ke halaman "laporan"
        Dashboard.setVisible(false);
        Obat.setVisible(false);
        DetailObat.setVisible(false);
        TambahObat.setVisible(false);
        Resep.setVisible(false);
        Dokter.setVisible(false);
        TambahDokter.setVisible(false);
        Laporan.setVisible(true);
        colorku();
        btn_laporan.setBackground(clicked);
    } else {
        JOptionPane.showMessageDialog(this, "Anda tidak dapat mengakses fitur laporan.");
    }
    }                                           

    private void btn_obatActionPerformed(java.awt.event.ActionEvent evt) {                                         
        // TODO add your handling code here:
        Dashboard.setVisible(false);
        Obat.setVisible(true);
        DetailObat.setVisible(false);
        TambahObat.setVisible(false);
        refresh_inputObat();
        colorku();
        btn_obat.setBackground(clicked);
        Resep.setVisible(false);
        Dokter.setVisible(false);
        TambahDokter.setVisible(false);
        DetailDokter.setVisible(false);
        Laporan.setVisible(false);
    }                                        

    private void btntambah_obatActionPerformed(java.awt.event.ActionEvent evt) {                                               
        // TODO add your handling code here:
        TambahObat.setVisible(true);
        Dashboard.setVisible(false);
        Obat.setVisible(false);
        DetailObat.setVisible(false);
        TambahObat.setVisible(true);
        txt_namaobat.requestFocus();
        colorku();
        btn_obat.setBackground(clicked);
        Resep.setVisible(false);
        Dokter.setVisible(false);
        TambahDokter.setVisible(false);
        Laporan.setVisible(false);
    }                                              

    private void tabel_obatMouseClicked(java.awt.event.MouseEvent evt) {                                        
        // TODO add your handling code here:
        int row = tabel_obat.rowAtPoint(evt.getPoint());
        String kd = tabel_obat.getValueAt(row, 0).toString();
        kodeobat.setText(kd);
        String nama = tabel_obat.getValueAt(row, 1).toString();
        namaobat.setText(nama);
        String harga = tabel_obat.getValueAt(row, 2).toString();
        hargaobat.setText(harga);
        String jenis = tabel_obat.getValueAt(row, 3).toString();
        jenisobat.setText(jenis);
        String stok = tabel_obat.getValueAt(row, 4).toString();
        stokobat.setText(stok);
        
        tampil_table_obat();
        Obat.setVisible(false);
        DetailObat.setVisible(true);
    }                                       

    private void kodeobatActionPerformed(java.awt.event.ActionEvent evt) {                                         
        // TODO add your handling code here:
    }                                        

    private void namaobatActionPerformed(java.awt.event.ActionEvent evt) {                                         
        // TODO add your handling code here:
    }                                        

    private void hargaobatActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:
    }                                         

    private void jenisobatActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:
    }                                         

    private void stokobatActionPerformed(java.awt.event.ActionEvent evt) {                                         
        // TODO add your handling code here:
    }                                        

    private void btn_hapusobatActionPerformed(java.awt.event.ActionEvent evt) {                                              
        // TODO add your handling code here:
        try {
            int konfir = JOptionPane.showConfirmDialog(this, "Apakah kamu yakin menghapus aku?","Pesan", JOptionPane.YES_NO_OPTION);
            if(konfir == JOptionPane.YES_OPTION){
                String sql = "DELETE FROM obat WHERE kdobat = '" + kodeobat.getText() + "'";
                java.sql.Connection conn = (Connection) Config.koneksi.configDBek();
                java.sql.PreparedStatement pst = conn.prepareStatement(sql);
                pst.execute();
                tampil_table_obat();
                DetailObat.setVisible(false);
                Obat.setVisible(true);
                JOptionPane.showMessageDialog(null, "Kamu tega banget!");
            }
        } catch (Exception e) {
            System.out.println("gagal dihapus data obat "+e.getMessage());
        }
    }                                             

    private void btn_ubahobatActionPerformed(java.awt.event.ActionEvent evt) {                                             
        // TODO add your handling code here:
        try {
            int konfir = JOptionPane.showConfirmDialog(this, "Apakah kamu yakin mengganti aku?","Pesan", JOptionPane.YES_NO_OPTION);
            if(konfir == JOptionPane.YES_OPTION){
                String sql = "UPDATE obat SET namaobat='"+namaobat.getText()+"', harga='"+hargaobat.getText()+"', "
                        + "stok='"+stokobat.getText()+"', jenis='"+jenisobat.getText()+"' WHERE kdobat='"+kodeobat.getText()+"'";
                java.sql.Connection conn = (Connection) Config.koneksi.configDBek();
                java.sql.PreparedStatement pst = conn.prepareStatement(sql);
                pst.executeUpdate(sql);
                tampil_table_obat();
                DetailObat.setVisible(false);
                Obat.setVisible(true);
                JOptionPane.showMessageDialog(null, "Kamu jahat banget!");
            }
        } catch (Exception e) {
            System.out.println("gagal diubah "+e.getMessage());
        }
    }                                            

    private void txt_kodeobatActionPerformed(java.awt.event.ActionEvent evt) {                                             
        // TODO add your handling code here:
    }                                            

    private void txt_namaobatActionPerformed(java.awt.event.ActionEvent evt) {                                             
        // TODO add your handling code here:
    }                                            

    private void txt_hargaobatActionPerformed(java.awt.event.ActionEvent evt) {                                              
        // TODO add your handling code here:
    }                                             

    private void txt_jenisobatActionPerformed(java.awt.event.ActionEvent evt) {                                              
        // TODO add your handling code here:
    }                                             

    private void txt_stokobatActionPerformed(java.awt.event.ActionEvent evt) {                                             
        // TODO add your handling code here:
    }                                            

    private void btn_simpanobatActionPerformed(java.awt.event.ActionEvent evt) {                                               
        // TODO add your handling code here:
        try {
                java.sql.Connection conn = (Connection) Config.koneksi.configDBek();
                Statement stmt = conn.createStatement();
                String sql = "INSERT INTO obat (kdobat, namaobat, harga, jenis, stok) VALUES ('"+txt_kodeobat.getText()+"',"
                        + " '"+txt_namaobat.getText()+"', '"+txt_hargaobat.getText()+"', '"+txt_jenisobat.getText()+"',"
                        + " '"+txt_stokobat.getText()+"')";
                stmt.executeUpdate(sql);
                stmt.close();
                conn.close();
                tampil_table_obat();
                refresh_inputObat();
                Obat.setVisible(true);
                TambahObat.setVisible(false);
                JOptionPane.showMessageDialog(this, "Data OKE, disimpan");
        } catch (Exception e) {
            System.out.println("gagal disimpan "+e.getMessage());
        }
    }                                              

    private void tabel_dokterMouseClicked(java.awt.event.MouseEvent evt) {                                          
        // TODO add your handling code here:
        int row = tabel_dokter.rowAtPoint(evt.getPoint());
        String id = tabel_dokter.getValueAt(row, 0).toString();
        iddokter.setText(id);
        String nama = tabel_dokter.getValueAt(row, 1).toString();
        namadokter.setText(nama);
        String spesialis = tabel_dokter.getValueAt(row, 2).toString();
        spesialisdokter.setText(spesialis);
        String telp = tabel_dokter.getValueAt(row, 3).toString();
        telpdokter.setText(telp);
        
        tampil_tableDokter();
        Dokter.setVisible(false);
        DetailDokter.setVisible(true);
    }                                         

    private void btn_tambahdokterActionPerformed(java.awt.event.ActionEvent evt) {                                                 
        // TODO add your handling code here:
        TambahDokter.setVisible(true);
        Dashboard.setVisible(false);
        Obat.setVisible(false);
        DetailObat.setVisible(false);
        TambahObat.setVisible(false);
        txt_namadokter.requestFocus();
        colorku();
        btn_dokter.setBackground(clicked);
        Resep.setVisible(false);
        Dokter.setVisible(false);
        Laporan.setVisible(false);        
    }                                                

    private void txt_iddokterActionPerformed(java.awt.event.ActionEvent evt) {                                             
        // TODO add your handling code here:
    }                                            

    private void txt_namadokterActionPerformed(java.awt.event.ActionEvent evt) {                                               
        // TODO add your handling code here:
    }                                              

    private void txt_spesialisdokterActionPerformed(java.awt.event.ActionEvent evt) {                                                    
        // TODO add your handling code here:
    }                                                   

    private void txt_telpdokterActionPerformed(java.awt.event.ActionEvent evt) {                                               
        // TODO add your handling code here:
    }                                              

    private void btn_simpandokterActionPerformed(java.awt.event.ActionEvent evt) {                                                 
        // TODO add your handling code here:
        try {
                JOptionPane.showMessageDialog(this, "Data dokter tidak boleh ada yang kosong");
                java.sql.Connection conn = (Connection) Config.koneksi.configDBek();
                Statement stmt = conn.createStatement();
                String sql = "INSERT INTO dokter (iddokter, namadokter, spesialis, telp) VALUES ('"+txt_iddokter.getText()+"',"
                        + " '"+txt_namadokter.getText()+"', '"+txt_spesialisdokter.getText()+"', '"+txt_telpdokter.getText()+"')";
                stmt.executeUpdate(sql);
                stmt.close();
                conn.close();
                tampil_tableDokter();
                refresh_inputDokter();
                Dokter.setVisible(true);
                TambahDokter.setVisible(false);
                JOptionPane.showMessageDialog(this, "Data OKE, disimpan");
        } catch (Exception e) {
            System.out.println("gagal disimpan  "+e.getMessage());
        }
    }                                                

    private void iddokterActionPerformed(java.awt.event.ActionEvent evt) {                                         
        // TODO add your handling code here:
    }                                        

    private void namadokterActionPerformed(java.awt.event.ActionEvent evt) {                                           
        // TODO add your handling code here:
    }                                          

    private void spesialisdokterActionPerformed(java.awt.event.ActionEvent evt) {                                                
        // TODO add your handling code here:
    }                                               

    private void telpdokterActionPerformed(java.awt.event.ActionEvent evt) {                                           
        // TODO add your handling code here:
    }                                          

    private void btn_hapusdokterActionPerformed(java.awt.event.ActionEvent evt) {                                                
        // TODO add your handling code here:
        try {
            int konfir = JOptionPane.showConfirmDialog(this, "Apakah kamu yakin menghapus aku?","Pesan", JOptionPane.YES_NO_OPTION);
            if(konfir == JOptionPane.YES_OPTION){
                String sql = "DELETE FROM dokter WHERE iddokter = '" + iddokter.getText() + "'";
                java.sql.Connection conn = (Connection) Config.koneksi.configDBek();
                java.sql.PreparedStatement pst = conn.prepareStatement(sql);
                pst.execute();
                tampil_tableDokter();
                DetailDokter.setVisible(false);
                Dokter.setVisible(true);
                JOptionPane.showMessageDialog(null, "Kamu tega banget!");
            }
        } catch (Exception e) {
            System.out.println("gagal dihapus data obat "+e.getMessage());
        }
    }                                               

    private void btn_ubahdokterActionPerformed(java.awt.event.ActionEvent evt) {                                               
        // TODO add your handling code here:
    }                                              

    private void btn_keluarActionPerformed(java.awt.event.ActionEvent evt) {                                           
        // TODO add your handling code here:
        Login.loginAll login = new Login.loginAll();
        login.setVisible(true);
        this.setVisible(false);
    }                                          

    /**
     * @param args the command line arguments
     */
    public static void main(String args[]) {
        /* Set the Nimbus look and feel */
        //<editor-fold defaultstate="collapsed" desc=" Look and feel setting code (optional) ">
        /* If Nimbus (introduced in Java SE 6) is not available, stay with the default look and feel.
         * For details see http://download.oracle.com/javase/tutorial/uiswing/lookandfeel/plaf.html 
         */
        try {
            for (javax.swing.UIManager.LookAndFeelInfo info : javax.swing.UIManager.getInstalledLookAndFeels()) {
                if ("Nimbus".equals(info.getName())) {
                    javax.swing.UIManager.setLookAndFeel(info.getClassName());
                    break;
                }
            }
        } catch (ClassNotFoundException ex) {
            java.util.logging.Logger.getLogger(DashboardAdmin.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (InstantiationException ex) {
            java.util.logging.Logger.getLogger(DashboardAdmin.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (IllegalAccessException ex) {
            java.util.logging.Logger.getLogger(DashboardAdmin.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (javax.swing.UnsupportedLookAndFeelException ex) {
            java.util.logging.Logger.getLogger(DashboardAdmin.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        }
        //</editor-fold>

        /* Create and display the form */
        java.awt.EventQueue.invokeLater(new Runnable() {
            public void run() {
                new DashboardAdmin().setVisible(true);
            }
        });
    }

    // Variables declaration - do not modify                     
    private javax.swing.JLabel BG;
    private javax.swing.JPanel Dashboard;
    private javax.swing.JPanel DetailDokter;
    private javax.swing.JPanel DetailObat;
    private javax.swing.JPanel Dokter;
    private javax.swing.JLabel Jpanel111;
    private javax.swing.JPanel Laporan;
    private javax.swing.JPanel Obat;
    private javax.swing.JPanel Resep;
    private javax.swing.JPanel TambahDokter;
    private javax.swing.JPanel TambahObat;
    private javax.swing.JTextField Teks;
    private Swing.btnroundkotakcb btn_dashboard;
    private Swing.btnroundkotakcb btn_dokter;
    private Swing.btnroundkotak btn_hapusdokter;
    private Swing.btnroundkotak btn_hapusobat;
    private Swing.btnroundkotakcb btn_keluar;
    public Swing.btnroundkotakcb btn_laporan;
    private Swing.btnroundkotakcb btn_obat;
    private Swing.btnroundkotakcb btn_resep;
    private Swing.btnroundkotak btn_simpandokter;
    private Swing.btnroundkotak btn_simpanobat;
    private Swing.btnroundkotak btn_tambahdokter;
    private Swing.btnroundkotak btn_ubahdokter;
    private Swing.btnroundkotak btn_ubahobat;
    private Swing.btnroundkotak btntambah_obat;
    private javax.swing.JTextField hargaobat;
    private javax.swing.JTextField iddokter;
    private javax.swing.JLabel jLabel10;
    private javax.swing.JLabel jLabel11;
    private javax.swing.JLabel jLabel3;
    private javax.swing.JLabel jLabel4;
    private javax.swing.JLabel jLabel5;
    private javax.swing.JLabel jLabel7;
    private javax.swing.JLabel jLabel8;
    private javax.swing.JLabel jLabel9;
    private javax.swing.JScrollPane jScrollPane1;
    private javax.swing.JScrollPane jScrollPane2;
    private javax.swing.JTextField jenisobat;
    private javax.swing.JTextField kodeobat;
    private javax.swing.JTextField namadokter;
    private javax.swing.JTextField namaobat;
    public javax.swing.JTextField namauser;
    private javax.swing.JTextField spesialisdokter;
    public javax.swing.JTextField status;
    private javax.swing.JTextField stokobat;
    private javax.swing.JTable tabel_dokter;
    private javax.swing.JTable tabel_obat;
    private javax.swing.JTextField telpdokter;
    private javax.swing.JTextField txt_hargaobat;
    private javax.swing.JTextField txt_iddokter;
    private javax.swing.JTextField txt_jenisobat;
    private javax.swing.JTextField txt_kodeobat;
    private javax.swing.JTextField txt_namadokter;
    private javax.swing.JTextField txt_namaobat;
    private javax.swing.JTextField txt_spesialisdokter;
    private javax.swing.JTextField txt_stokobat;
    private javax.swing.JTextField txt_telpdokter;
    // End of variables declaration                   
}
