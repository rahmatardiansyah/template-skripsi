\subsection{Segmentasi}

Menurut \textcite{IPI1759345} menjelaskan bahwa tepi atau edge pada pengolahan citra digital merujuk pada perubahan mendadak nilai intensitas derajat keabuan dalam jarak yang dekat. Sebuah titik dapat dikategorikan sebagai tepi ketika memperlihatkan perbedaan nilai piksel yang signifikan dengan nilai piksel tetangganya. Untuk mendeteksi tepi dalam citra digital, diperlukan operasi \textit{edge detection} guna mengenali garis tepi yang membatasi wilayah citra homogen yang memiliki perbedaan tingkat kecerahan. Dalam bidang pengolahan citra, deteksi tepi menjadi hal yang penting karena berperan dalam menghasilkan tepi-tepi pada obyek citra digital.Beberapa teknik untuk mendeteksi tepi:

\begin{enumerate}[leftmargin=1cm, itemindent=0.6cm,labelwidth=15pt, labelsep=5pt, listparindent=1cm,align=left]

    \item Operator \textit{Roberts}


          Operator Roberts adalah operator yang berbasis gradien yang menggunakan dua buah kernel yang berukuran 2x2 piksel. Operator ini mengambil arah diagonal untuk penentuan arah dalam penghitungan nilai gradien, sehingga sering disebut dengan operator silang \textcite{mulyanto2009teori}.

          \begin{figure*}[ht]
    	      \includegraphics[width=0.85\textwidth, center]{images/Robert.png}
    	      \caption{Operator Robert}
          \end{figure*}

          Bentuk dari operator \textit{roberts} ditunjukkan pada gambar 2.1. Misal f adalah citra yang akan dikenai operator \textit{roberts}. Maka, nilai operator Robert pada (y, x) didefinisikan sebagai

          \begin{equation}
    	      r(y,x) = \sqrt{(z_1 - z_4)^2 + (z_3 - z_2)^2}
          \end{equation}

          Dalam hal ini, z1 = f(y,x), z2 = f(y,x+1), z3 = f(y+1,x), dan z4 = f(y+1,x+1).

    \item Operator \textit{Prewitt}

          \begin{figure*}[ht]
    	      \includegraphics[width=0.85\textwidth, center]{images/Prewitt.png}
    	      \caption{Operator Prewitt}
          \end{figure*}

          Metode \textit{Prewitt} merupakan pengembangan dari metode Robert yang ditemukan oleh Prewitt pada tahun 1966. Metode \textit{Prewitt} menggunakan filter HPF (\textit{High Pass Filter}) yang diberi satu angka nol penyangga. Metode ini mengambil prinsip dari fungsi laplacian sebagai fungsi untuk membangkitkan HPF (\textit{High Pass Filter}). Kernel filter yang digunakan dalam metode Prewitt ini bisa dilihat pada gambar 2.2.

          Bentuk dari operator \textit{prewitt} ditunjukkan pada gambar 2.2. Misal f adalah citra yang akan dikenai operator \textit{prewitt}. Maka, nilai operator prewitt pada (y, x) didefinisikan sebagai

          \begin{equation}
    	      r(y,x) =
    	      \sqrt{
    		      \begin{aligned}
    			      (f(y-1,x-1)+f(y,x-1)+f(y+1,x-1)    \\
    			      -f(y-1,x+1)-f(y,x+1)-f(y+1,x+1))^2 \\
    			      +(f(y+1,x-1)+f(y+1,x)+f(y+1,x+1)   \\
    			      -f(y-1,x-1)-f(y-1,x)-f(y-1,x+1))^2
    		      \end{aligned}
    	      }
          \end{equation}

    \item Operator \textit{Sobel}

          Operator \textit{sobel} adalah operator yang banyak digunakan sebagai pendeteksian tepi karena kesederhanaannya. Operator \textit{sobel} merupakan pengembangan dari operator \textit{robert} yang diberi satu angka nol penyangga. Berbeda dengan operator \textit{prewitt} yang lebih sensitif terhadap tepi vertikal dan horizontal, operator \textit{sobel} lebih sensitif terdapap tepi diagonal. Kelebihan dari metode \textit{sobel} ini adalah kemampuan untuk mengurangi \textit{noise} sebelum melakukan perhitungan pendeteksian tepi.

          \begin{figure*}[ht]
    	      \includegraphics[width=0.85\textwidth, center]{images/Sobel.png}
    	      \caption{Operator Sobel}
          \end{figure*}

          Operator sobel adalah magnitude dari gradien yang dihitung dengan

          \begin{equation}
    	      M =
    	      \sqrt{
    		      \begin{aligned}
    			      S_x^2+S_y^2
    		      \end{aligned}
    	      }
          \end{equation}

          Keterangan

          M = Besar gradien operator sobel

          Sx = Gradien \textit{sobel} arah horizontal

          Sy = Gradien \textit{sobel} arah vertikal

    \item Operator \textit{Laplacian}

          Operator Laplacian merupakan operator turunan kedua yang bersifat omnidirectional, yakni menebalkan bagian tepi ke segala arah. Namun, operator Laplacian memiliki kelemahan yakni peka terhadap derau, memberikan ketebalan ganda dan tidak mampu mendeksi arah tepi \cite{kadir2013pengolahan}.

          \begin{figure*}[ht]
    	      \includegraphics[width=0.85\textwidth, center]{images/Laplacian.png}
    	      \caption{Operator Laplacian}
          \end{figure*}


          Berdasarkan cadar \#1 pada gambar 2.4(a), nilai operator Laplacian pada (y,x) didefinisikan sebagai

          \begin{equation}
    	      l(y,x) =
    	      \begin{aligned}
    		      4f(y,x)-[f(y-1,x)+f(y,x-1)+f(y,x+1)+f(y+1,x)]
    	      \end{aligned}
          \end{equation}

    \item Operator \textit{Canny}

          Operator Canny ditemukan oleh John Canny pada tahun 1986 yang terkenal sebagai operator deteksi tepi yang optimal. Algoritma ini memberikan tingkat kesalahan yang rendah. Terdapat enam langkah yang dilakukan untuk mengimplementasikan deteksi tepi Canny. Langkah tersebut dijabarkan sebagai berikut

          \begin{figure*}[ht]
    	      \includegraphics[width=0.85\textwidth, center]{images/Canny.png}
    	      \caption{Operator Canny}
          \end{figure*}

          \begin{enumerate}
    	      \item Langkah 1

    	            Pertama dilakukan penapisan terhadap citra dengan tujuan untuk menghilangkan derau menggunakan filter Gaussian dengan kadar sederhana dengan ketentuan kadar yang digunakan berukuran jauh lebih kecil dari pada ukuran citra.

    	      \item Langkah 2

    	            Setelah penghalus gambar terhadap derau dilakukan, selanjutnya proses mendapatkan kekutan tepi (edge strenght) dengan menggunakan operator Gaussian. Gradien citra dapat dihitung dengan rumus

    	            \begin{equation}
    		            \left | G \right | = \left | Gx \right | + \left | Gy \right |
    	            \end{equation}

    	      \item Langkah 3

    	            Menghitung arah tepi. Rumus yang digunakan adalah

    	            \begin{equation}
    		            theta= \tan ^{-1}(GxGy)
    	            \end{equation}

    	      \item Langkah 4

    	            Menghubungkan arah tepi dengan sebuah arah yang dapat dilacak citra.

    	      \item Langkah 5

    	            Proses hysteresis, proses ini menghilangkan garis-garis yang terputus.
          \end{enumerate}

\end{enumerate}
