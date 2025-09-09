# Bermain-dengan-data-titanic
# Menambahkan variabel baru: Ukuran Keluarga (Family Size)
# Ini adalah jumlah saudara/pasangan (sibsp) + orang tua/anak (parch) + diri sendiri (1)
titanic['family_size'] = titanic['sibsp'] + titanic['parch'] + 1

# Menambahkan variabel baru: Sendirian (is_alone)
# Ini didasarkan pada kolom 'family_size'
titanic['is_alone'] = (titanic['family_size'] == 1).astype(int)

# Menampilkan beberapa baris pertama untuk verifikasi
print("\nDataset dengan Kolom 'family_size' dan 'is_alone':")
print(titanic[['sibsp', 'parch', 'family_size', 'is_alone']].head())

# Visualisasi distribusi variabel 'is_alone'
plt.figure(figsize=(8, 6))
sns.countplot(x='is_alone', data=titanic, palette='viridis')
plt.title("Distribusi Penumpang yang Bepergian Sendirian vs. Bersama Keluarga")
plt.xlabel("Sendirian (1) / Bersama Keluarga (0)")
plt.ylabel("Jumlah Penumpang")
plt.xticks([0, 1], ['Bersama Keluarga', 'Sendirian']) # Mengganti label sumbu x
plt.show()
