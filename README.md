Nama : Addnan Nurwakhid
Nim  : 19.11.2736

# StudiKasusUAS
Aplikasi ini bertujuan seperti simulasi pembelian makanan dan minuman dengan menggunakan promo/voucher.
# How Does It Works? 
- User dapat melihat daftar makanan dan minuman yang tersedia
- User dapat melihat voucher yang di tawarkan
- User dapat menggunakan voucher
- User dapat melihat potongan harga setelah menggunakan salh satu voucher

Dimulai dari Penawaran.xaml.cs yg bertujuan untuk menawarkan sebuah list makanan yang bisa menggunakan sebuah voucher untuk di tampilkan di listbox.
```c++
private void generateContentPenawaran()
        {
            Item coffeLate = new Item("Coffe Late", 30000);
            Item blackTea = new Item("BlackTea", 20000);
            Item milkShake = new Item("Milk Shake", 15000);
            Item watermelonJuice = new Item("Watermelon Juice", 25000);
            Item lemonSquash = new Item("Lemon Squash", 30000);
            Item pizza = new Item("Pizza", 75000);
            Item friedRice = new Item("Fried Rice Special", 45000);
        }
```
Lalu pada MainWindow.xaml.cs kita menginisiasi object dari Penawaran.xaml.cs dan juga Voucher.xaml.cs, 
untuk di masukan dalam sebuah list KeranjangBelanja.
Dan tampilan Total dari semua belanja akan di tampilkan pada ListBox.
```c++
 public MainWindow()
        {
            InitializeComponent();

            payment = new Payment(this);
            payment.setBalance(500000);
            payment.setPromo(0);

            KeranjangBelanja keranjangBelanja = new KeranjangBelanja(payment, this);

            controller = new MainWindowController(keranjangBelanja);

            listBoxPesanan.ItemsSource = controller.getSelectedItems();
            listBoxPakaiVoucher.ItemsSource = controller.getSelectedVouchers();

            initializeView();

        }

        private void initializeView()
        {
            labelSubtotal.Content = 0;
            labelGrantTotal.Content = 0;
            labelPromoFee.Content = (payment.getPromo() > 0) ? - payment.getPromo() : 0;
        }

        public void onPenawaranSelected(Item item)
        {
            controller.addItem(item);
        }
```

Terimakasih..!
