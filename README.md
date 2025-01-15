import numpy as np

# Definisikan fungsi f(x) dan turunannya f'(x)
def f(x, p):
    return x**2 - p

def f_prime(x):
    return 2*x

# Fungsi Newton-Raphson untuk mencari akar
def newton_raphson(p, tol=1e-6):
    # Tentukan tebakan awal x0
    x0 = p / 2
    # Inisialisasi iterasi
    iteration = 0
    
    # Lakukan iterasi hingga |f(x)| < tol
    while True:
        # Hitung f(x) dan f'(x)
        fx = f(x0, p)
        fx_prime = f_prime(x0)
        
        # Hitung nilai x selanjutnya
        x1 = x0 - fx / fx_prime
        
        # Cek apakah sudah memenuhi toleransi
        if np.abs(fx) < tol:  # menggunakan np.abs
            break
        
        # Update x0 untuk iterasi berikutnya
        x0 = x1
        iteration += 1
    
    return x1, iteration

# Nilai p yang diberikan
p = 1.16 + 10

# Hitung akar menggunakan metode Newton-Raphson
root, iterations = newton_raphson(p)

# Tampilkan hasil
print(f"Akar fungsi f(x) = x^2 - {p} ditemukan di x = {root}")
print(f"Jumlah iterasi: {iterations}")
