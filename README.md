# Tugas-UAS-Metode-Numerik
Code coding untuk UAS Metode Numerik - Ikrar Aji Setyawan
import numpy as np 

p = 21
x0 = p / 2
toleransi = 1e-6
max_iter = 100

#Fungsi f(x) dan turunannya f'(x)
def f(x):
    return np.power(x, 2) - p  # f(x) = x^2 - p

def f_prime(x):
    return 2 * x  # f'(x) = 2x

#NR Iterasi
x_n = x0
iterasi_data = []

for i in range(max_iter):
    f_x_n = f(x_n)  # Hitung nilai f(x_n)
    f_prime_x_n = f_prime(x_n)  # Hitung nilai f'(x_n)
    iterasi_data.append((i, x_n, f_x_n, f_prime_x_n))  # Simpan data iterasi

    #Periksa apakah sudah memenuhi toleransi
    if np.abs(f_x_n) < toleransi:
        break

    #Perbarui nilai x_n menggunakan formula NR
    x_n = x_n - f_x_n / f_prime_x_n

print("Hasil Akar:", x_n)
print("Total Iterasi:", i)

#Menampilkan tabel iterasi
print("\nIterasi | x_n       | f(x_n)        | f'(x_n)")
for data in iterasi_data:
    print(f"{data[0]:7d} | {data[1]:.6f} | {data[2]:.6f} | {data[3]:.6f}")
