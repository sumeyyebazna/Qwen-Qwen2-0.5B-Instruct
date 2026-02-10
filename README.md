Amaç: Öğrenci yanlış cevap verdiğinde modelin:
1) Yanlış olduğunu belirtmesi  
2) Hata türünü sınıflandırması  
3) Doğru yaklaşımı öğretmesi  

Bu repo, **Google Colab + Tesla T4 (~15GB)** koşullarında çalışacak şekilde, küçük ölçekli bir **CausalLM** modelini (varsayılan: `Qwen/Qwen2-0.5B-Instruct`) **FP32 stabil eğitim** ile fine-tune etmek için hazırlanmıştır.

## 1) Kurulum (Colab)
Colab hücresinde:
```bash
bash scripts/colab_setup.sh
```

## 2) Veri (Alpaca JSONL)
`data/` klasörüne şu dosyaları koyun:
- `mega_dataset_alpaca_train.jsonl`
- `mega_dataset_alpaca_val.jsonl`

Her satır JSON objesi:
```json
{"instruction":"...","input":"...","output":"..."}
```

## 3) Eğitim
```bash
python src/train.py
```

Çıktı: `outputs/finetuned/`

> Not: Varsayılan eğitim **FP32** yürür. NaN/Inf guard + gradient clipping + gradient accumulation vardır.

## 4) Inference
```bash
python src/infer.py
```


