# Prediccion de Prendas con TensorFlow.js

Este proyecto usa un modelo entrenado en Python con TensorFlow/Keras y convertido a TensorFlow.js para predecir dibujos hechos en una interfaz web.

El modelo fue entrenado con el dataset Fashion MNIST, por eso reconoce prendas como camiseta, pantalon, sueter, vestido, abrigo, sandalia, camisa, tenis, bolso y botin.

## Estructura del proyecto

pagina_modelo/
  index.html
  README.md
  tfjs_target_dir/
    model.json
    group1-shard1of1.bin

## Requisitos

Necesitas tener instalado Python para levantar un servidor local.

Verifica que Python funcione con:

python --version

## Como ejecutar el proyecto

Abre una terminal dentro de la carpeta pagina_modelo y ejecuta:

python -m http.server 8000

Luego abre el navegador en:

http://localhost:8000

## Como usar la interfaz

1. Dibuja una prenda dentro del cuadro blanco.
2. Presiona el boton Predecir.
3. La pagina mostrara la clase predicha y el porcentaje de confianza.
4. Usa Limpiar para borrar el dibujo y probar otro.

## Archivos importantes

- index.html: contiene la interfaz, el canvas para dibujar y el codigo JavaScript que carga el modelo.
- tfjs_target_dir/model.json: descripcion del modelo convertido a TensorFlow.js.
- tfjs_target_dir/group1-shard1of1.bin: pesos del modelo.

## Como se genero el modelo

En Google Colab se entreno un modelo con TensorFlow/Keras y luego se exporto con:

modelo.export("modelo_savedmodel")

Despues se convirtio a TensorFlow.js con:

tensorflowjs_converter \
  --input_format=tf_saved_model \
  --output_format=tfjs_graph_model \
  --signature_name=serve \
  modelo_savedmodel \
  tfjs_target_dir

## Nota importante

El modelo fue entrenado con imagenes reales del dataset Fashion MNIST, no con dibujos hechos a mano. Por eso algunas predicciones pueden no ser exactas si el dibujo no se parece a las imagenes del dataset.

Para mejorar los resultados, dibuja la prenda grande, centrada y con trazos claros.
