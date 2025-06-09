<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Kalkulator Tarif Efektif Rata-Rata (TER)</title>
</div>
  <style>
  body {
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
    margin: 0;
    background-color: #f5f5f5;
  }
.header {
    background-color: #002147; /* Biru tua ala DJP */
    color: white;
    text-align: center;
    padding: 2rem 1rem 1rem;
    border-bottom: 5px solid #ffc107; /* Gold garis bawah */
  }

.header h1 {
    font-size: 32px;
    font-weight: 700;
    margin: 0;
  }

  .header p {
    font-size: 16px;
    font-weight: 400;
    margin-top: 0.5rem;
  }

 .container {
    max-width: 700px;
    background: white;
    margin: 2rem auto;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 0 12px rgba(0, 0, 0, 0.05);
  }
   label {
    display: block;
    margin-bottom: 0.3rem;
    font-weight: 600;
    color: #333;
  }

input, select {
    width: 100%;
    padding: 6px 10px;
    margin-bottom: 1.2rem;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 14px;
    box-sizing: border-box;
  }
    button {
  background-color: #FFD700;
  color: #002147;
  font-weight: bold;
  border: none;
  padding: 0.75rem;
  border-radius: 5px;
  cursor: pointer;
  transition: background 0.3s ease;
}
button:hover {
  background-color: #e6c200;
}
 .result {
    margin-top: 2rem;
    background: #e9f0f7;
    border-left: 4px solid #002147;
    padding: 1rem;
    border-radius: 4px;
  }
   .result p {
    margin: 0.5rem 0;
  }
  </style>
</head>
<body>
<div class="header">
  <h1>PT INDOTEX</h1>
  <p>Kalkulator Pajak Tarif Efektif Rata-Rata (TER)</p>
</div>

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
<input type="text" id="jenisTER" readonly />

<label for="tarifTER">Tarif TER (%)</label>
<input type="text" id="tarifTER" readonly />

<button onclick="hitungTER()">Calculate</button>
<button onclick="printResult()">Cetak Hasil ke PDF</button>

<div class="result" id="output"></div>

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
    { min: 10050000, max: 10350000, tarif: 2.25 },
    { min: 10350000, max: 10700000, tarif: 2.5 },
    { min: 10700000, max: 11050000, tarif: 3 },
    { min: 11050000, max: 11600000, tarif: 3.5 },
    { min: 11600000, max: 12500000, tarif: 4 },
    { min: 12500000, max: 13750000, tarif: 5 },
    { min: 13750000, max: 15100000, tarif: 6 },
    { min: 15100000, max: 16950000, tarif: 7 },
    { min: 16950000, max: 19750000, tarif: 8 },
    { min: 19750000, max: 24150000, tarif: 9 },
    { min: 24150000, max: 26450000, tarif: 10 },
    { min: 26450000, max: 28000000, tarif: 11 },
    { min: 28000000, max: 30050000, tarif: 12 },
    { min: 30050000, max: 32400000, tarif: 13 },
    { min: 32400000, max: 35400000, tarif: 14 },
    { min: 35400000, max: 39100000, tarif: 15 },
    { min: 39100000, max: 43850000, tarif: 16 },
    { min: 43850000, max: 47800000, tarif: 17 },
    { min: 47800000, max: 51400000, tarif: 18 },
    { min: 51400000, max: 56300000, tarif: 19 },
    { min: 56300000, max: 62200000, tarif: 20 },
    { min: 62200000, max: 68600000, tarif: 21 },
    { min: 68600000, max: 77500000, tarif: 22 },
    { min: 77500000, max: 89000000, tarif: 23 },
    { min: 89000000, max: 103000000, tarif: 24 },
    { min: 103000000, max: 125000000, tarif: 25 },
    { min: 125000000, max: 157000000, tarif: 26 },
    { min: 157000000, max: 206000000, tarif: 27 },
    { min: 206000000, max: 337000000, tarif: 28 },
    { min: 337000000, max: 454000000, tarif: 29 },
    { min: 454000000, max: 550000000, tarif: 30 },
    { min: 550000000, max: 695000000, tarif: 31 },
    { min: 695000000, max: 910000000, tarif: 32 },
    { min: 910000000, max: 1400000000, tarif: 33 },
    { min: 1400000000, max: Infinity, tarif: 34 }
  ],
  B: [
    { min: 0, max: 6200000, tarif: 0 },
    { min: 6200000, max: 6500000, tarif: 0.25 },
    { min: 6500000, max: 6850000, tarif: 0.5 },
    { min: 6850000, max: 7300000, tarif: 0.75 },
    { min: 7300000, max: 9200000, tarif: 1 },
    { min: 9200000, max: 10750000, tarif: 1.5 },
    { min: 10750000, max: 11250000, tarif: 2 },
    { min: 11250000, max: 11600000, tarif: 2.5 },
    { min: 11600000, max: 12600000, tarif: 3 },
    { min: 12600000, max: 13600000, tarif: 4 },
    { min: 13600000, max: 14950000, tarif: 5 },
    { min: 14950000, max: 16400000, tarif: 6 },
    { min: 16400000, max: 18450000, tarif: 7 },
    { min: 18450000, max: 21850000, tarif: 8 },
    { min: 21850000, max: 26000000, tarif: 9 },
    { min: 26000000, max: 27700000, tarif: 10 },
    { min: 27700000, max: 29350000, tarif: 11 },
    { min: 29350000, max: 31450000, tarif: 12 },
    { min: 31450000, max: 33950000, tarif: 13 },
    { min: 33950000, max: 37100000, tarif: 14 },
    { min: 37100000, max: 41100000, tarif: 15 },
    { min: 41100000, max: 45800000, tarif: 16 },
    { min: 45800000, max: 49500000, tarif: 17 },
    { min: 49500000, max: 53800000, tarif: 18 },
    { min: 53800000, max: 58500000, tarif: 19 },
    { min: 58500000, max: 64000000, tarif: 20 },
    { min: 64000000, max: 71000000, tarif: 21 },
    { min: 71000000, max: 80000000, tarif: 22 },
    { min: 80000000, max: 93000000, tarif: 23 },
    { min: 93000000, max: 109000000, tarif: 24 },
    { min: 109000000, max: 129000000, tarif: 25 },
    { min: 129000000, max: 163000000, tarif: 26 },
    { min: 163000000, max: 211000000, tarif: 27 },
    { min: 211000000, max: 374000000, tarif: 28 },
    { min: 374000000, max: 459000000, tarif: 29 },
    { min: 459000000, max: 555000000, tarif: 30 },
    { min: 555000000, max: 704000000, tarif: 31 },
    { min: 704000000, max: 957000000, tarif: 32 },
    { min: 957000000, max: 1405000000, tarif: 33 },
    { min: 1405000000, max: Infinity, tarif: 34 }
  ],
  C: [
    { min: 0, max: 6600000, tarif: 0 },
    { min: 6600000, max: 6950000, tarif: 0.25 },
    { min: 6950000, max: 7350000, tarif: 0.5 },
    { min: 7350000, max: 7800000, tarif: 0.75 },
    { min: 7800000, max: 8850000, tarif: 1 },
    { min: 8850000, max: 9800000, tarif: 1.25 },
    { min: 9800000, max: 10950000, tarif: 1.5 },
    { min: 10950000, max: 11200000, tarif: 1.75 },
    { min: 11200000, max: 12050000, tarif: 2 },
    { min: 12050000, max: 12950000, tarif: 3 },
    { min: 12950000, max: 14150000, tarif: 4 },
    { min: 14150000, max: 15550000, tarif: 5 },
    { min: 15550000, max: 17050000, tarif: 6 },
    { min: 17050000, max: 19500000, tarif: 7 },
    { min: 19500000, max: 22700000, tarif: 8 },
    { min: 22700000, max: 26600000, tarif: 9 },
    { min: 26600000, max: 28100000, tarif: 10 },
    { min: 28100000, max: 30100000, tarif: 11 },
    { min: 30100000, max: 32600000, tarif: 12 },
    { min: 32600000, max: 35400000, tarif: 13 },
    { min: 35400000, max: 38900000, tarif: 14 },
    { min: 38900000, max: 43000000, tarif: 15 },
    { min: 43000000, max: 47400000, tarif: 16 },
    { min: 47400000, max: 51200000, tarif: 17 },
    { min: 51200000, max: 55800000, tarif: 18 },
    { min: 55800000, max: 60400000, tarif: 19 },
    { min: 60400000, max: 66700000, tarif: 20 },
    { min: 66700000, max: 74500000, tarif: 21 },
    { min: 74500000, max: 83200000, tarif: 22 },
    { min: 83200000, max: 95600000, tarif: 23 },
    { min: 95600000, max: 110000000, tarif: 24 },
    { min: 110000000, max: 134000000, tarif: 25 },
    { min: 134000000, max: 169000000, tarif: 26 },
    { min: 169000000, max: 221000000, tarif: 27 },
    { min: 221000000, max: 390000000, tarif: 28 },
    { min: 390000000, max: 463000000, tarif: 29 },
    { min: 463000000, max: 561000000, tarif: 30 },
    { min: 561000000, max: 709000000, tarif: 31 },
    { min: 709000000, max: 965000000, tarif: 32 },
    { min: 965000000, max: 1419000000, tarif: 33 },
    { min: 1419000000, max: Infinity, tarif: 34 }
  ]
};

    function hitungTER() {
  const brutoBulanan = parseInt(document.getElementById("penghasilan").value);
  const statusPTKP = parseInt(document.getElementById("statusPTKP").value);

  const jenis = brutoBulanan <= 10000000 ? 'A' : brutoBulanan <= 20000000 ? 'B' : 'C';
  document.getElementById("jenisTER").value = jenis;

  const nama = document.getElementById("nama").value;
  const npwp = document.getElementById("npwp").value;
  const nik = document.getElementById("nik").value;
  const jabatan = document.getElementById("jabatan").value;
  const alamat = document.getElementById("alamat").value;
  const telepon = document.getElementById("telepon").value;
  const email = document.getElementById("email").value;

  const output = document.getElementById("output");
  const tarifField = document.getElementById("tarifTER");
  const tarifObj = tarifTER[jenis].find(d => brutoBulanan >= d.min && brutoBulanan < d.max);

  if (!tarifObj) {
    output.innerHTML = '<p>Tarif tidak ditemukan.</p>';
    tarifField.value = '';
    return;
  }
  const ter = tarifObj.tarif;
  tarifField.value = ter;

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
function printResult() {
    const hasil = document.getElementById("output").innerHTML;
    const style = `
      <style>
        body { font-family: Arial, sans-serif; padding: 2rem; }
        h3 { text-align: center; }
        p { margin: 0.5rem 0; }
      </style>
    `;

    const win = window.open('', '', 'height=800,width=600');
    win.document.write('<html><head><title>Hasil Perhitungan Pajak</title>');
    win.document.write(style);
    win.document.write('</head><body>');
    win.document.write(hasil);
    win.document.write('</body></html>');
    win.document.close();
    win.print();
  }
  </script>
</body>
</html>
