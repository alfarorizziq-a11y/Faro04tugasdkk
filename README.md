import streamlit as st
import math

st.set_page_config(page_title="Kalkulator Bangun Ruang Simple", page_icon="📐")
st.title("🧮 Kalkulator Bangun Ruang Simple")
st.caption("Hitung volume dan luas permukaan dengan mudah")

menu = st.selectbox(
    "Pilih Bangun Ruang:",
    ["Kubus", "Balok", "Tabung", "Kerucut", "Bola", "Prisma Segitiga"]
)

st.divider()

# ================== KUBUS ==================
if menu == "Kubus":
    s = st.number_input("Panjang sisi:", min_value=0.0)
    if st.button("Hitung"):
        volume = s ** 3
        luas = 6 * s ** 2
        st.success(f"Volume: {volume}")
        st.info(f"Luas Permukaan: {luas}")

# ================== BALOK ==================
elif menu == "Balok":
    p = st.number_input("Panjang:", min_value=0.0)
    l = st.number_input("Lebar:", min_value=0.0)
    t = st.number_input("Tinggi:", min_value=0.0)
    if st.button("Hitung"):
        volume = p * l * t
        luas = 2 * (p*l + p*t + l*t)
        st.success(f"Volume: {volume}")
        st.info(f"Luas Permukaan: {luas}")

# ================== TABUNG ==================
elif menu == "Tabung":
    r = st.number_input("Jari-jari:", min_value=0.0)
    t = st.number_input("Tinggi:", min_value=0.0)
    if st.button("Hitung"):
        volume = math.pi * r**2 * t
        luas = 2 * math.pi * r * (r + t)
        st.success(f"Volume: {volume:.2f}")
        st.info(f"Luas Permukaan: {luas:.2f}")

# ================== KERUCUT ==================
elif menu == "Kerucut":
    r = st.number_input("Jari-jari:", min_value=0.0)
    t = st.number_input("Tinggi:", min_value=0.0)
    s = math.sqrt(r**2 + t**2)
    if st.button("Hitung"):
        volume = (1/3) * math.pi * r**2 * t
        luas = math.pi * r * (r + s)
        st.success(f"Volume: {volume:.2f}")
        st.info(f"Luas Permukaan: {luas:.2f}")

# ================== BOLA ==================
elif menu == "Bola":
    r = st.number_input("Jari-jari:", min_value=0.0)
    if st.button("Hitung"):
        volume = (4/3) * math.pi * r**3
        luas = 4 * math.pi * r**2
        st.success(f"Volume: {volume:.2f}")
        st.info(f"Luas Permukaan: {luas:.2f}")

# ================== PRISMA SEGITIGA ==================
elif menu == "Prisma Segitiga":
    alas = st.number_input("Alas segitiga:", min_value=0.0)
    tinggi_segitiga = st.number_input("Tinggi segitiga:", min_value=0.0)
    sisi_miring = st.number_input("Sisi miring:", min_value=0.0)
    tinggi_prisma = st.number_input("Tinggi prisma:", min_value=0.0)

    if st.button("Hitung"):
        luas_alas = 0.5 * alas * tinggi_segitiga
        volume = luas_alas * tinggi_prisma
        luas = (2 * luas_alas) + (alas + tinggi_segitiga + sisi_miring) * tinggi_prisma
        st.success(f"Volume: {volume}")
        st.info(f"Luas Permukaan: {luas}")
