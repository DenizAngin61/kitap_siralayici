# kitap_siralayici

import java.util.*;

// Book sınıfını oluşturuyoruz ve Comparable arayüzünden kalıtım alıyoruz.
class Book implements Comparable<Book> {
    private String name;        // Kitap ismi
    private int pageCount;      // Sayfa sayısı
    private String author;      // Yazarın ismi
    private String publishDate; // Yayın tarihi

    // Constructor: Yeni bir Book nesnesi oluşturmak için kullanılır.
    public Book(String name, int pageCount, String author, String publishDate) {
        this.name = name;
        this.pageCount = pageCount;
        this.author = author;
        this.publishDate = publishDate;
    }

    // Getter metodları: Özel değişkenlere dışarıdan erişim sağlamak için kullanılır.
    public String getName() {
        return name;
    }

    public int getPageCount() {
        return pageCount;
    }

    public String getAuthor() {
        return author;
    }

    public String getPublishDate() {
        return publishDate;
    }

    // toString metodu: Kitap bilgilerini yazdırmak için kullanılır.
    @Override
    public String toString() {
        return "Book{" +
                "name='" + name + '\'' +
                ", pageCount=" + pageCount +
                ", author='" + author + '\'' +
                ", publishDate='" + publishDate + '\'' +
                '}';
    }

    // compareTo metodu: Kitapları isme göre sıralamak için kullanılır.
    @Override
    public int compareTo(Book other) {
        return this.name.compareTo(other.name); // A'dan Z'ye sıralama
    }
}

public class Main {
    public static void main(String[] args) {
        // 5 tane kitap nesnesi oluşturuyoruz.
        Book book1 = new Book("1984", 328, "George Orwell", "1949");
        Book book2 = new Book("To Kill a Mockingbird", 281, "Harper Lee", "1960");
        Book book3 = new Book("The Great Gatsby", 180, "F. Scott Fitzgerald", "1925");
        Book book4 = new Book("Pride and Prejudice", 432, "Jane Austen", "1813");
        Book book5 = new Book("Moby Dick", 635, "Herman Melville", "1851");

        // Kitapları isme göre sıralamak için TreeSet kullanıyoruz.
        Set<Book> booksByName = new TreeSet<>();
        booksByName.add(book1);
        booksByName.add(book2);
        booksByName.add(book3);
        booksByName.add(book4);
        booksByName.add(book5);

        // İsme göre sıralanmış kitapları yazdırıyoruz.
        System.out.println("Kitaplar isme göre sıralandı:");
        for (Book book : booksByName) {
            System.out.println(book);
        }

        // Kitapları sayfa sayısına göre sıralamak için Comparator kullanıyoruz.
        Set<Book> booksByPageCount = new TreeSet<>(new Comparator<Book>() {
            @Override
            public int compare(Book b1, Book b2) {
                return Integer.compare(b1.getPageCount(), b2.getPageCount()); // Sayfa sayısına göre sıralama
            }
        });

        booksByPageCount.add(book1);
        booksByPageCount.add(book2);
        booksByPageCount.add(book3);
        booksByPageCount.add(book4);
        booksByPageCount.add(book5);

        // Sayfa sayısına göre sıralanmış kitapları yazdırıyoruz.
        System.out.println("\nKitaplar sayfa sayısına göre sıralandı:");
        for (Book book : booksByPageCount) {
            System.out.println(book);
        }
    }
}
