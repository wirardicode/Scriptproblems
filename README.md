# Read me 

Selamat datang di script uji neu dimana script ini bertujuan untuk membantu dalam memeberikan referensi script recreated,(Khusus neutron office).

## Tujuan
----------
Script ini ditujukan untuk membantu dalam membuat script pembuatan soal/problem pada `https://office.uji.neon.id/`, 

## Set Bahasa Dokumentasi
---
- Indonesia

## Dokumentasi
-------
    Daftar isi
        A. Membuat json dasar
        B. Membuat Pilihan ganda (single selection)
        C. Jawaban S  ingkat
        E. Jawaban Panjang
</br>

##### Membuat Pilihan ganda (single selection)
_____
Sebelum membuat rangkaian script dipastikan membuat json dasar yang terdiri dari,
1. `name` : merupakan bagian yang ditujukan untuk menamakan judul probles => (wajib)
2. `description` : ditujukan untuk membuat deskripsi pada problem => (tidak wajib)
3. `problems` : berisi array atau list permasalahan.
```bash
    "name": "Problem Set Name",
    "description": "Description of the problem set.",
    "problems": [
        {
        <<SOAL_DIMASUKAN_DI_SINI>>
        }
    ]
```

#### Membuat Pilihan ganda (single selection)
___
contoh script untuk single selection
```bash
    {
      "name": "SOAL 1",
      "description": "",
      "publishing": "published",
      "prompt":"Bisa diisi apa saja (Support HTML code snippet)" ,
      "kind": "choosing",
      "type": "choosingChoice || choosingChoices || choosingTrue/False || choosingChoice ||choosingYes/No || choosingSelect",
      "config": {
        "shuffleOptions": false || true
      },
      "identifier": "alphabe || number || roman",
      "options": [
        {
          "identifier": "A",
          "content": "3,75",
          "isCorrect": false,
          "point": 0
        },
        {
          "identifier": "B",
          "content": "37,5",
          "isCorrect": false,
          "point": 0
        },
      ]
    }
```
Hal wajib harus ada:
1. `name` : Judul soal ini ditujukan untuk per soal saja (tidak mempengaruhi soal lain)
1. `publishing` : status publish, terdiri dari 
1. `prompt` : soal yang akan dikerjan
1. `kind` : jenis soal
1. `type` : tipe soal
1. `config` : apakah soal diacak atau tidak
1. `identifier`: jenis pilihan mau ABCan Atau lain nya
1. `options`: pilihan ganda nya (jawaban yang akan dipilih) terdiri dari <b>identifier</b> adalah Pilihan jawabna (A/B/C), <b>content</b> merupakan isi atau value pilihan, <b>isCorrect</b> adalah boolean yang menunjukan pilihan itu salah atau benar, <b>point</b> bentuk dari skor atau bobot nilai dari tiap pilihan.

##### text
__________
script text pendek:
```bash
  {
      "name": "Problem name",
      "description": "Description of the problem.",
      "prompt": "soal",
      "publishing": "draft || published",
      "kind": "writing",
      "type": "writingShort",
      "config": {
        "lang": "any", //bahasa
        "caseSensitive": false,
        "match": "manual || keyword-answer || exact || answer-keyword || fuzzy",
        "min": 0,
        "max": 100,
        "keywords": [{
          "value": "Jawaban",
          "point":1
        }]
      },
      "pointCustom": null,
      "options": [], //?? tidak tau tidak ada di config manual
  }
```

#### text panjang
____

```bash
  {
      "name": "nama problem",
      "description": "",  //tidak penting
      "prompt": "soal",
      "publishing": "draft || published",
      "kind": "writing",
      "type": "writingLong",
      "explanation": "", //tidak penting
      "config": {
        "caseSensitive": false,
        "correct": "manual",
        "keywords": [
          {
            "id": "69ba0d176be751f92f0d6a05",
            "point": 1,
            "value": "jawaban"
          }
        ],
        "lang": "any",
        "match": "exact || manual || fuzzy",
        "max": 100,
        "min": 1,
        "minimums": { //pilih salah satu atau set semua
          "keyword": 1,
          "percentage": 0.5,
          "point": 1,
          "token": 1 
        },
        "token": "sentence || word"
      },
      "identifier": "",  //kebawah tidak wajib (nilai baka ke set deffault)
      "pointCustom": null,
      "options": [],
      "hints": [] 
    }
```
