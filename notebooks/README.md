# Notebooks / Scripts de carga a S3

Coloca aquí el notebook (Colab/Local) o script que:
1) Genera o transforma datos IoT (JSON)
2) Sube el fichero a `s3://<bucket>/data/sensores/<...>.json`

**Importante:** No subas credenciales ni tokens.

## Notebook listo para usar

Se incluye `notebooks/generate_upload_iot.ipynb`, que:
1) genera datos IoT sintéticos con el esquema solicitado, y
2) los sube a S3.

Pasos:
1. Abre `notebooks/generate_upload_iot.ipynb`.
2. Edita `AWS_REGION`, `S3_BUCKET`, `S3_KEY`.
3. Ejecuta todas las celdas.

Salida esperada:
- archivo local `iabd01_sensores.json`
- objeto en `s3://<bucket>/data/sensores/iabd01_sensores.json`

Valor que debes usar en la app/entrega:
- `S3_KEY=data/sensores/iabd01_sensores.json`
