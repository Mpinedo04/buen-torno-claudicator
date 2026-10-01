# Torno paralelo 3D: estado de la revisión

Archivo entregable: `torno-paralelo-3d.html` (un solo HTML, ~3 980 líneas, Three.js r128 de cdnjs).
API de depuración en la consola del navegador: `window.LATHE` (SIM, LIVE, ACT, DEMO, WP, NODE, PARTS, REQ, VIEW, select, goPreset…).

## Verificado en el navegador (funciona)
- Carga sin errores de consola. La autocomprobación de engranes no da avisos. Rendimiento: ~270 draw calls y ~324 k triángulos.
- Vistas: sólido, transparente (carcasas), alambre, corte con rayado de sección y explosionada.
- Selección por clic (raycast) con resaltado, atenuación del resto, contorno y vuelo de cámara. La ficha muestra todos los apartados y las piezas relacionadas son clicables. Funcionan el tooltip al pasar el ratón y el árbol con buscador (cajón en móvil).
- Etiquetas 3D con líneas guía, ya limitadas a piezas principales y sin solapes.
- Simulación:
  - Velocidad del husillo: 423,4 rpm, exacta.
  - Cilindrado: avance medido 0,1018 mm/rev, igual a la placa. El Ø baja de 50 a 48 y el volumen arrancado coincide con el teórico. Salen virutas.
  - Roscado: 1,5000 mm/rev exactos y relación patrón/husillo 0,5. El indicador de roscado se para con la tuerca cerrada. La 2.ª pasada cae en el mismo surco.
  - Pulgadas: la casilla 7-B da 8 h/" (3,175 mm). Las casillas no normalizadas salen marcadas y se ve el juego de ruedas de 127 Z.
- Enclavamientos:
  - Barra y tuerca partida se excluyen en ambos sentidos.
  - Velocidad y caja Norton bloqueadas en marcha.
  - Levantar el protector para el motor y la seta impide arrancar.
  - Se bloquea el movimiento manual contra la pieza con el husillo parado.
- Volantes SVG arrastrables: ¼ de vuelta del transversal = 0,625 mm.
- Barra nueva (aluminio Ø30): las garras se cierran y la demo acerca el contrapunto.
- Responsive: probado a 375×812 y 750 px de ancho, con cajones, dock plegado y la máquina entera en pantalla.

## Correcciones ya aplicadas durante la revisión
- La fusión de mallas estáticas absorbía la malla dinámica de la pieza, que se veía negra y no se actualizaba.
- Colores: suelo y bandeja pasados a lineal; acero en bruto más claro.
- Datos de corte: Q se dividía dos veces por la escala de tiempo; ap ahora es la profundidad real; la profundidad de rosca toma el radio correcto.
- Ficha en móvil: no se abría por especificidad CSS (#info frente a .open).
- Los clics atraviesan el policarbonato del protector del plato.
- Vistas predefinidas: se adaptan a pantallas estrechas y tienen un encuadre más bajo.
- Interfaz:
  - Dock más compacto y botones de los volantes que ya caben.
  - Pestañas desplazables y botón de ficha junto al de piezas.
  - Aviso cuando las rpm recomendadas superan la máxima del torno.
- Eliminado un cierre `})();` duplicado.

## Donde se quedó (interrumpido)
Prueba por JS de atajos de teclado (E, X, W, C, G, L, 1–6, H/Esc, flechas, Espacio) y de indexar la torreta. La llamada se cortó y no se sabe el resultado; **hay que repetirla**.

## Pendiente
1. Repetir la prueba de atajos de teclado y la de la torreta (ACT.tool).
2. Recargar y comprobar visualmente las últimas ediciones: botón ⓘ movido, pestañas desplazables, ancho de los volantes y texto de rpm máximas.
3. Probar con clics los mandos que aún no se han tocado:
   - Barra de corte: eje, deslizador e invertir.
   - Ayuda, overlay de FPS (tecla º/`) y selector de vistas.
   - Ángulo del orientable (cono con el carro superior).
   - Pestaña Contrapunto: bloqueo, posición, volante de la caña, bloqueo de caña y desplazamiento lateral.
   - Seta, sentido de giro, interruptores del protector y escala de tiempo.
   - Botones Aislar, Ocultar y Mostrar todas.
4. Captura final de escritorio a ≥1366×768 y lectura de FPS con el overlay.
5. Opcional:
   - Afinar algunos desplazamientos de la vista explosionada.
   - Revisar la orientación de los diales del eje X (orientable y caña).
6. Al terminar: quitar la emulación de viewport del panel y ofrecer publicarlo como Artifact privado.

## Simplificaciones conocidas (documentadas en las fichas)
- Al cerrar la tuerca partida, la fase de la rosca se sincroniza sola, como si se usara el indicador de roscado.
- En pulgadas solo algunas casillas Norton dan valores normalizados; el resto salen en gris.
- Las virutas que caen sobre el carro le siguen solo en X.
