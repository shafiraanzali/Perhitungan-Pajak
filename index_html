<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Kalkulator Tarif Efektif Rata-rata (TER)</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 2rem;
      background-color: #f4f4f4;
    }
    .container {
      max-width: 700px;
      margin: auto;
      background: white;
      padding: 2rem;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    label, select, input {
      display: block;
      margin-bottom: 1rem;
      width: 100%;
    }
    button {
      padding: 0.75rem;
      background: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    .result {
      margin-top: 1rem;
      padding: 1rem;
      background: #eef;
      border-radius: 5px;
    }
    .result p {
      margin: 0.5rem 0;
    }
    h2 {
      margin-top: 2rem;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Kalkulator Tarif Efektif Rata-rata (TER)</h2>

    <label>Nama Wajib Pajak</label>
    <input type="text" id="nama" placeholder="Contoh: Budi Santoso" />

    <label>NPWP</label>
    <input type="text" id="npwp" placeholder="Contoh: 12.345.678.9-012.000" />

    <label>NIK</label>
    <input type="text" id="nik" placeholder="Contoh: 1234567890123456" />

    <label>Jabatan</label>
    <input type="text" id="jabatan" placeholder="Contoh: Manajer Keuangan" />

    <label>Alamat Tempat Tinggal</label>
    <input type="text" id="alamat" placeholder="Contoh: Jl. Merdeka No. 10, Jakarta" />

    <label>Status Pernikahan</label>
    <select id="statusPernikahan">
      <option value="TK">Tidak Kawin</option>
      <option value="K">Kawin</option>
      <option value="K/I">Kawin (Penghasilan Istri Digabung)</option>
    </select>

    <label>Jumlah Tanggungan</label>
    <select id="tanggungan">
      <option value="0">0</option>
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
    </select>

    <label>Nomor Telepon/HP</label>
    <input type="text" id="telepon" placeholder="Contoh: 081234567890" />

    <label>Email</label>
    <input type="email" id="email" placeholder="Contoh: email@contoh.com" />

    <label for="penghasilan">Penghasilan Bruto Bulanan (Rp)</label>
    <input type="number" id="penghasilan" placeholder="Contoh: 8500000" />

    <label for="statusPTKP">Status PTKP</label>
    <select id="statusPTKP">
      <option value="54000000">TK/0 - Rp54.000.000</option>
      <option value="58500000">TK/1 - Rp58.500.000</option>
      <option value="63000000">TK/2 - Rp63.000.000</option>
      <option value="67500000">TK/3 - Rp67.500.000</option>
      <option value="58500000">K/0 - Rp58.500.000</option>
      <option value="63000000">K/1 - Rp63.000.000</option>
      <option value="67500000">K/2 - Rp67.500.000</option>
      <option value="72000000">K/3 - Rp72.000.000</option>
      <option value="112500000">K/I/0 - Rp112.500.000</option>
      <option value="117000000">K/I/1 - Rp117.000.000</option>
      <option value="121500000">K/I/2 - Rp121.500.000</option>
      <option value="126000000">K/I/3 - Rp126.000.000</option>
    </select>

    <label for="jenisTER">Jenis TER</label>
    <select id="jenisTER">
      <option value="A">TER A</option>
      <option value="B">TER B</option>
      <option value="C">TER C</option>
    </select>

    <button onclick="hitungTER()">Hitung TER & Pajak</button>

    <div class="result" id="output"></div>
  </div>

  <script>
    const tarifTER = {
      A: [
        { min: 0, max: 5400000, tarif: 0 },
        { min: 5400000, max: 5650000, tarif: 0.25 },
        { min: 5650000, max: 5950000, tarif: 0.5 },
        { min: 5950000, max: 6300000, tarif: 0.75 },
        { min: 6300000, max: 6750000, tarif: 1 },
        { min: 6750000, max: 7500000, tarif: 1.25 },
        { min: 7500000, max: 8550000, tarif: 1.5 },
        { min: 8550000, max: 9650000, tarif: 1.75 },
        { min: 9650000, max: 10050000, tarif: 2 },
        { min: 1400000000, max: Infinity, tarif: 34 },
      ],
      B: [
        { min: 0, max: 6200000, tarif: 0 },
        { min: 6200000, max: 6500000, tarif: 0.25 },
        { min: 6500000, max: 6850000, tarif: 0.5 },
        { min: 6850000, max: 7300000, tarif: 0.75 },
        { min: 7300000, max: 9200000, tarif: 1 },
        { min: 1405000000, max: Infinity, tarif: 34 },
      ],
      C: [
        { min: 0, max: 6600000, tarif: 0 },
        { min: 6600000, max: 6950000, tarif: 0.25 },
        { min: 6950000, max: 7350000, tarif: 0.5 },
        { min: 7350000, max: 7800000, tarif: 0.75 },
        { min: 1419000000, max: Infinity, tarif: 34 },
      ]
    };

    function hitungTER() {
      const jenis = document.getElementById("jenisTER").value;
      const brutoBulanan = parseInt(document.getElementById("penghasilan").value);
      const statusPTKP = parseInt(document.getElementById("statusPTKP").value);

      const nama = document.getElementById("nama").value;
      const npwp = document.getElementById("npwp").value;
      const nik = document.getElementById("nik").value;
      const jabatan = document.getElementById("jabatan").value;
      const alamat = document.getElementById("alamat").value;
      const status = document.getElementById("statusPernikahan").value;
      const tanggungan = document.getElementById("tanggungan").value;
      const telepon = document.getElementById("telepon").value;
      const email = document.getElementById("email").value;

      const output = document.getElementById("output");
      const tarifObj = tarifTER[jenis].find(d => brutoBulanan >= d.min && brutoBulanan < d.max);

      if (!tarifObj) {
        output.innerHTML = '<p>Tarif tidak ditemukan.</p>';
        return;
      }

      const ter = tarifObj.tarif;
      const brutoTahunan = brutoBulanan * 12;
      const pkp = Math.max(0, brutoTahunan - statusPTKP);
      const pajakTahunan = (ter / 100) * brutoTahunan;
      const pajakBulanan = pajakTahunan / 12;

      output.innerHTML = `
        <h3>Hasil Perhitungan TER & Pajak</h3>
        <p><strong>Nama Wajib Pajak:</strong> ${nama}</p>
        <p><strong>NPWP:</strong> ${npwp}</p>
        <p><strong>NIK:</strong> ${nik}</p>
        <p><strong>Jabatan:</strong> ${jabatan}</p>
        <p><strong>Alamat:</strong> ${alamat}</p>
        <p><strong>Status Perkawinan:</strong> ${status}</p>
        <p><strong>Jumlah Tanggungan:</strong> ${tanggungan}</p>
        <p><strong>No HP:</strong> ${telepon}</p>
        <p><strong>Email:</strong> ${email}</p>
        <hr />
        <p><strong>Jenis TER:</strong> ${jenis}</p>
        <p><strong>Tarif TER:</strong> ${ter}%</p>
        <p><strong>Penghasilan Bruto Tahunan:</strong> Rp ${brutoTahunan.toLocaleString('id-ID')}</p>
        <p><strong>PTKP:</strong> Rp ${statusPTKP.toLocaleString('id-ID')}</p>
        <p><strong>PKP (Penghasilan Kena Pajak):</strong> Rp ${pkp.toLocaleString('id-ID')}</p>
        <p><strong>Pajak Terutang Tahunan:</strong> Rp ${pajakTahunan.toLocaleString('id-ID')}</p>
        <p><strong>Pajak Bulanan:</strong> Rp ${pajakBulanan.toLocaleString('id-ID')}</p>
      `;
    }
  </script>
</body>
</html>

