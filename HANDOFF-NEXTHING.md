# HANDOFF NEXTHING: contexto completo y estado actual

Para el Claude que continúe este proyecto. Este documento describe **solo el estado vigente** (9-nov-2026, noche): qué existe hoy, cómo funciona, qué está decidido y qué falta. No incluye versiones descartadas ni errores ya resueltos.

Dueña: **Camila Corral Ronquillo**. Cuenta de Shopify y DSers: camilacor0504@gmail.com. Idioma: español de México. Hora local: Ciudad Juárez, Chihuahua.

---

## 1. REGLAS DE CAMILA (obligatorias)

1. **Nunca comprar nada.** "Comprueba todo lo que necesites, pero no cobres ni pagues nada." Los pagos (AliExpress, DSers, Shopify, PayPal, dominio) los hace ella.
2. **No publicar, activar ni modificar nada de la tienda sin su autorización explícita.**
   - Productos nuevos: NO agregar a DSers, NO importar a Shopify, NO publicar, NO activar, NO hacer visibles, NO cambiar precios/descripciones/configuración de productos existentes.
   - Solo después de su visto bueno **individual por producto** se puede agregar a DSers y preparar la incorporación a Shopify; y **aun así no se publica ni se hace visible** hasta que lo autorice expresamente.
3. **No escribir contraseñas ni iniciar sesión por ella.** La sesión de DSers está cerrada; ella debe iniciar sesión (la pantalla de login aparece con el correo prellenado). Tampoco se crean cuentas ni se ingresan datos financieros.
4. **Canal de venta:** Instagram y Facebook, con **Meta Ads pagados**. Sin TikTok. Sin personas reales en los creativos (producto, animación o ilustración sí). En Facebook no se marca el contenido como "hecho con IA" (indicación de Camila).
5. **Sin reseñas falsas, sin certificaciones o especificaciones inventadas, sin precio tachado ficticio.** Solo reseñas reales (Judge.me).
6. **Meta no admite afirmaciones de salud:** nada de "alivia el dolor", "cura", "elimina contracturas", ni preguntar "¿te duele la espalda?". El copy habla del producto y la comodidad, no de padecimientos.
7. **No cambiar el precio de la pistola (MX$699)** salvo que ella lo pida.
8. La marca debe poder vender **productos de todo tipo**. Los nuevos productos deben ser de un **nicho parecido** (carga, energía y accesorios tecnológicos simples).
9. Camila es directa: respuestas claras, con datos verificados, y decir expresamente qué es suposición y qué no se pudo confirmar.

---

## 2. EL NEGOCIO

- **Tienda:** NEXTHING, dropshipping solo para **México**. https://nexthingis.myshopify.com (admin: https://admin.shopify.com/store/nexthingis). Moneda MXN. Pública y funcionando.
- **Tema en vivo:** "Copia de Horizon" (id 194819227927), basado en el tema Horizon. El tema anterior "Horizon" quedó en borrador como respaldo (Tienda online > Temas > publicar "Horizon" para volver atrás).
- **Producto vigente:** pistola de masaje de mango largo y curvo, 4 cabezales, recargable USB-C, **MX$699** (Negro y Plateado). ID Shopify 15492483318039. URL: `/products/pistola-de-masaje-mango-largo`. Costo registrado en Shopify: MX$341.
- **Proveedor:** Yan Xu Store (AliExpress, anuncio 1005010766883317). Respaldo: DAQI Beautylife Store (1005008497519039). Conectado con **DSers plan Basic** (gratis; el pedido se arma manualmente con un clic en DSers cuando hay una compra; el plan Advanced cuesta US$19.9/mes y Camila decidió no contratarlo).
- **Variantes mapeadas en DSers:** Negro = "Black", Plateado = "Silvery" del anuncio de Yan Xu. Falta verificar el costo de Plateado con el primer pedido.
- **Contacto público:** nexthingsoporte@gmail.com (único correo). Sin teléfono publicado y sin WhatsApp (no hay número comercial). Instagram: instagram.com/nexthing.shop. Facebook: página "Nexthing" (id 61596214507976).
- **Datos legales:** Camila Corral Ronquillo, Río Álamo 726, Las Arcadas, C.P. 32563, Ciudad Juárez, Chihuahua. Sin RFC público. Precios con IVA incluido.
- **Pagos (Shopify Payments):** Shop Pay, Visa, Mastercard, American Express, Apple Pay, Google Pay y Maestro. **PayPal aparece en el checkout pero su configuración está incompleta**: Camila debe terminarlo o quitarlo.
- **Envío:** "Envío gratis a todo México", tarifa de México = gratis. Entrega prometida: **10 a 15 días hábiles** desde la confirmación del pago, con número de rastreo. Procesamiento 1 a 2 días hábiles.

### Economía de la pistola
- Venta MX$699. Costo: DSers mostró MX$340.79 (285.11 producto + 55.68 envío, 12 a 17 días); AliExpress mostraba MX$256.72 con envío gratis y llegada 20-25 nov, promo que termina 18-nov, 4.7★ con 768 valoraciones, vendedor 89.2 % positivas, "solo quedan 8". Se usa 341 como costo.
- Utilidad aproximada MX$277 por pedido antes de anuncios (comisión Shopify Payments 3.6 % + MX$3 y ~8 % de reembolsos/disputas) ≈ 40 %.
- **Hay que confirmar costo real, stock y tiempo real con el primer pedido de un cliente real.**

---

## 3. CÓMO ESTÁ CONSTRUIDA LA TIENDA (tema "Copia de Horizon")

### Archivos del tema con código propio
- `sections/nx-home.liquid` — portada. Scripts y CSS propios **antes de `{% schema %}`**:
  - Tarjeta **"Lo más nuevo"** con el producto, botón "Comprar ahora" y **calificación promedio de Judge.me** (estrellas y número, tomados de la página del producto).
  - **Cuadro flotante de reseñas en carrusel** junto a la tarjeta (scroll-snap, puntos de navegación, se posiciona sin tapar otros textos; se alimenta solo de reseñas reales de Judge.me; si hay más reseñas se puede deslizar).
  - **Etiqueta navideña** roja y dorada: "Un buen regalo para relajar a tus seres queridos estas navidades" con moño; se oculta sola después del **7-ene-2027**.
  - Título de la tarjeta acortado en móvil (corta en " | ").
  - Bloque para que la portada móvil no "salte" al cargar: oculta `<main>` hasta que se agrega la clase `nx-ready` (tope 2 s).
  - Catálogo que se llena solo desde `/collections/all/products.json` (etiqueta "Nuevo" si tiene menos de 30 días, descuento solo si existe precio de comparación), categorías si existen, bloque editorial y FAQ.
- `layout/theme.liquid` — variables de color (paleta), estilos del tema, capa de movimiento (respeta `prefers-reduced-motion`), bloque de confianza `#nx-trust` en el producto, botón propio **"Comprar ahora"** y barra fija de compra en móvil.
  - `#nx-trust` incluye beneficios, logos de pago, soporte y la línea **"Entrega estimada: 10 a 15 días hábiles"** debajo del botón de compra.
  - "Comprar ahora" vacía el carrito, agrega la variante y cantidad elegidas y manda directo a `/checkout`; debajo dice "Pago seguro con tarjeta · Sin crear cuenta". El botón morado de pago exprés de Shop Pay está oculto en la página de producto.
- `locales/es.json` — textos de envío del carrito: "Envío gratis a todo México." (8 cadenas).
- `config/settings_data.json` — logo (alto 60 px en PC, 46 en móvil), tipografía DM Sans, favicon.
- `templates/index.json` — orden del inicio: encabezado, beneficios, producto, preguntas. Imágenes del hero (`image_1` PC, `image_1_mobile`). Primer beneficio: "Tecnología que masajea por ti". Botón del hero lleva directo al producto.
- `templates/page.contact.json` — botón del formulario "Enviar mensaje".
- `sections/header-group.json` — barra de anuncios: **"Súper oferta: $699 · Envío gratis a todo México · Garantía de 90 días"**.
- `sections/footer-group.json` — íconos sociales desactivados; pie con correo, Instagram y Facebook.

### Menús y páginas
- Menú principal: Inicio, La pistola, Contacto. Menú de pie: las 5 políticas + Buscar.
- Páginas: **Sobre NEXTHING** (/pages/sobre-nexthing) y **Contacto** (/pages/contact, id 179255476503). Contacto tiene tarjetas (correo de soporte, tiempo de respuesta de 24 h hábiles, garantía), lista de qué incluir en el mensaje y enlaces a políticas.
- Pantalla de contraseña ya no aplica (tienda pública).

### Texto vigente de "Sobre NEXTHING" (inicio)
"Lo siguiente que vas a querer, directo a tu puerta. NEXTHING es una tienda de productos prácticos que trabajan por ti, con envío a todo México. Elegimos cada producto pensando en que sea fácil de usar y que te resuelva algo del día a día. Hoy empezamos con nuestra pistola de masaje de mango largo y 4 cabezales, y vamos a seguir sumando productos. Lo que te prometimos: Envío gratis a todo México. Entrega en 10 a 15 días hábiles, con número de rastreo. Garantía de 90 días contra defectos de fabricación…"

### FAQ de la portada (texto vigente)
- ¿Cuánto tarda el envío? Entre 10 y 15 días hábiles a todo México. El envío es gratis y recibes un número de rastreo.
- ¿Qué garantía tienen los productos? 90 días contra defectos de fabricación, con cambio o reembolso conforme a la ley.
- ¿Puedo devolver mi compra? Puedes revocar tu compra dentro de 5 días hábiles de recibirla.
- ¿Cómo puedo pagar? Con tarjeta, de forma segura y sin necesidad de crear una cuenta.
- ¿Cómo los contacto? Escríbenos a nexthingsoporte@gmail.com con tu número de pedido y te respondemos lo antes posible.

---

## 4. LA FICHA DEL PRODUCTO (texto exacto vigente)

**Título:** Pistola de masaje con mango largo para espalda | Inalámbrica, 4 cabezales
**Precio:** MX$699 (sin precio de comparación). **Variantes:** Negro, Plateado (ambas MX$699, disponibles). **Imágenes:** 11. **Proveedor/vendor:** NEXTHING. Categoría: Masajeadores eléctricos.

**Descripción:**
> Tecnología que masajea por ti. Su mango largo y curvo llega a tu espalda, tus hombros y tu cuello sin que tengas que pedir ayuda, y sus pulsaciones de percusión trabajan por ti para darte un masaje cómodo y práctico, cuando quieras y donde quieras.
> Presiona, elige tu cabezal y disfruta.
>
> **Por qué te va a gustar**
> - Mango largo y curvo: alcanza espalda, hombros y cuello tú solo(a).
> - 4 cabezales intercambiables (esfera, plano, en Y y punta): uno para cada zona.
> - Percusión para relajar los músculos después del trabajo, del gimnasio o de un día largo.
> - Recargable por USB-C.
> - Dos colores a elegir: negro o plateado.
>
> **Cómo usarla**
> - Carga la pistola por USB-C antes de usarla.
> - Elige el cabezal para la zona que quieres trabajar.
> - Enciéndela y deslízala con suavidad sobre el músculo, en sesiones cortas por zona. Su mango largo y curvo te permite alcanzar espalda, hombros y cuello tú solo(a).
>
> **Especificaciones**
> - Tipo: pistola de masaje de percusión con mango largo y curvo.
> - Cabezales incluidos: 4 intercambiables (esfera, plano, en Y y punta).
> - Niveles de intensidad: 9.
> - Batería: recargable de litio, 1200 mAh.
> - Carga: por USB, tiempo de carga de 2 a 3 horas.
> - Potencia nominal: 20 W (5 V, 1 A).
> - Materiales: ABS y silicona.
> - Colores: negro o plateado.
> - Garantía: 90 días contra defectos de fabricación.
>
> **Compra con tranquilidad**
> - Envío gratis a todo México, con número de rastreo.
> - Entrega estimada: de 10 a 15 días hábiles desde la confirmación del pago. Si es para regalo de Navidad, pídela con tiempo.
> - Garantía de 90 días contra defectos de fabricación, con cambio o reembolso conforme a la ley.
> - Puedes revocar tu compra dentro de 5 días hábiles de recibirla.
> - Atención por mensaje a todas horas, con respuesta en máximo 24 horas hábiles.
>
> Recomendaciones de uso: carga la pistola antes de usarla y úsala en sesiones cortas por zona. Es un producto de uso personal para relajación muscular y no sustituye la atención médica. Consulta a tu médico antes de usarla si estás embarazada, usas marcapasos o tienes una lesión o condición de salud. No la uses sobre huesos, piel dañada o zonas inflamadas.

**Origen de las especificaciones:** descripción técnica del proveedor (modelo GB-868). **No publicadas por no estar confirmadas:** autonomía (el anuncio la da ambigua), peso, ruido y dimensiones. No decir "silencioso", "99 velocidades", "horas de batería", "recomendado por médicos". Confirmar con el primer pedido.

**Galería (11 imágenes):** fotos del proveedor sin personas, imágenes propias en español con logo (cabezales, mango y controles, mango largo, colores, especificaciones, "lo que incluye"), y "cómo se usa" (foto de uso generada con IA, sin rostro). Archivos en `imagenes-tienda/`. Pendiente: reordenar a mano la galería (colocar "cómo se usa" en la posición 3).

---

## 5. POLÍTICAS (texto vigente en Shopify)

URLs: `/policies/refund-policy`, `/policies/privacy-policy`, `/policies/terms-of-service`, `/policies/shipping-policy`, `/policies/contact-information`. Editables en admin: `settings/legal/<refund|privacy|terms-of-service|shipping|contact-information>`. Todas usan el correo **nexthingsoporte@gmail.com**; ninguna muestra teléfono. El domicilio aparece en Privacidad, Términos e Información de contacto (obligación de la LFPC, art. 76 Bis).

**Cancelación, devoluciones y reembolsos:**
> Cancelación antes del envío: puedes cancelar tu pedido antes de que lo enviemos y te devolvemos el 100% de tu pago. Derecho de revocación (LFPC art. 56): puedes revocar tu compra dentro de los 5 días hábiles posteriores a recibir el producto, sin responsabilidad. Escríbenos a nexthingsoporte@gmail.com con tu número de pedido y te daremos las instrucciones. Devuelve el producto completo, sin uso y en su empaque. Los gastos de flete y seguro de la devolución corren por cuenta del cliente. Al recibir el producto te devolvemos el precio pagado. Producto defectuoso, incompleto o distinto al ofrecido (art. 92): si tu producto no corresponde a lo anunciado o llega dañado, escríbenos con fotos o video dentro de 30 días naturales. Puedes elegir entre la reposición del producto o la devolución de tu dinero, y te corresponde una bonificación conforme a la ley. En estos casos no pagas el envío de regreso. Garantía (art. 77): todos nuestros productos tienen garantía de 90 días a partir de la entrega contra defectos de fabricación. Para hacerla válida escribe a nexthingsoporte@gmail.com con tu número de pedido y evidencia del defecto. No cubre daños por mal uso, golpes o modificaciones. Reembolsos: se hacen por el mismo medio de pago de la compra. El tiempo en que lo veas reflejado depende de tu banco (normalmente de 3 a 10 días hábiles). Contacto: nexthingsoporte@gmail.com. Atención por mensaje; respondemos en máximo 24 horas hábiles.

**Política de envío:**
> Enviamos únicamente dentro de México. Procesamos tu pedido en 1 a 2 días hábiles después de confirmar el pago. El tiempo de entrega estimado se indica en la página de cada producto, en días hábiles contados desde la confirmación del pago. Te enviamos el número de rastreo por correo dentro de 48 horas hábiles después de que salga tu pedido. El envío está incluido en el precio mostrado; no se cobran cargos adicionales al pagar. Si tu pedido no llega dentro del tiempo de entrega indicado más 5 días hábiles, escríbenos: investigamos con la paquetería y, si no se localiza, reponemos el producto o te devolvemos tu dinero completo. Revisa que tu dirección sea correcta. Si el paquete se devuelve por dirección incorrecta o falta de recepción, te contactaremos para reenviarlo. Algunos productos pueden llegar en más de un paquete; te avisaremos con los números de rastreo. Contacto: nexthingsoporte@gmail.com. Atención por mensaje; respondemos en máximo 24 horas hábiles.

**Información de contacto:**
> Operada por: Camila Corral Ronquillo. Domicilio: Río Álamo 726, Las Arcadas, C.P. 32563, Ciudad Juárez, Chihuahua, México. Correo: nexthingsoporte@gmail.com. Horario: atención por mensaje a todas horas; respondemos en máximo 24 horas hábiles. Para reclamaciones o aclaraciones puedes contactarnos por cualquiera de estos medios. También puedes acudir a la Procuraduría Federal del Consumidor (Profeco).

**Privacidad (aviso integral propio) y Términos:** contenido completo en `politicas-nexthing.md` (se pueden leer actualizados en las URLs anteriores).

---

## 6. RESEÑAS (Judge.me, plan gratuito)

- Solo reseñas **reales**. Hay 3: Ivana M (Camila confirmó que es real), mari y Daniel. El promedio y el carrusel de la portada salen de estas.
- Widget en el producto con el formulario "Escribir una reseña", todo en español salvo la etiqueta **"YouTube URL"** (cambiar en Judge.me > Idioma).
- Judge.me manda correo automático de solicitud tras la compra, con el logo de NEXTHING (el plan gratis no permite editar colores ni textos).
- Mensajes para pedir reseñas reales: `mensajes-para-pedir-resenas.md`. Regla: nunca escribir ni condicionar reseñas; si alguien recibió el producto gratis o con descuento, que lo declare.
- No se importaron reseñas de AliExpress ni de otras fuentes.
- En la vista previa del editor del tema, Judge.me muestra reseñas de ejemplo que no aparecen en la tienda pública.

---

## 7. IDENTIDAD DE MARCA

- **Logo oficial:** "N" + NEXTHING. Archivos en `logo/`: logo navy y negro (con versiones HD), íconos, favicon, foto de perfil de Facebook y portada de Facebook v2.
- **Paleta "Holst" (tienda):** #0D1B2A, #1B263B, #415A77, #778D7A, #D4C4A8 (beige solo en detalles), #F4F1DE. **Anuncios:** texto y botón navy #0A1B2E, subtítulos #34506D, fondo blanco/gris claro azulado (#F2F6FB a #C4D2E1).
- **Tipografías:** DM Sans en la tienda. Anuncios e imágenes: Lato (y DM Serif Display en los posts de Facebook).
- **Tono:** cálido, directo, mexicano neutro, tuteo.
- Nombre en Facebook: "Nexthing" (Facebook no acepta todo en mayúsculas).

---

## 8. MARKETING DE LA PISTOLA

### Anuncios finales (carpeta `anuncios-meta/`)
Fondo blanco, textos en navy, logo arriba y etiqueta pequeña **"SÚPER OFERTA | $699 MXN"** (sin precio tachado). Tres diseños, cada uno en 3 formatos: `_cuadrado` 1080×1080 (Feed/Marketplace), `_feed` 1080×1350 (4:5 Feed Facebook/Instagram), `_historia` 1080×1920 (Historias y Reels; textos fuera de la zona que tapa la interfaz).
- `d-masaje-profundo` — "Masaje profundo, sin complicaciones." (las dos pistolas)
- `g-tu-ritmo` — "Tu masaje, a tu ritmo."
- `f-tecnologia` — "La tecnología también llegó a tus masajes"
- Enlace de destino: https://nexthingis.myshopify.com/products/pistola-de-masaje-mango-largo
- Nota: una "súper oferta" sin fecha de fin puede cuestionarse (PROFECO/Meta): definir cuándo termina o llamarla "precio especial".

### Titulares aprobados (salen de la lista de frases de Camila)
Tecnología que masajea por ti · Potencia en cada movimiento · Masaje profundo, sin complicaciones · ¡Tu espalda merece este masaje! · La tecnología también llegó a tus masajes · Tu masaje, a tu ritmo · Relajación en cada pulsación · Presiona, elige tu cabezal y disfruta.

### Textos principales (primary text)
1. "¡La tecnología también llegó a tus masajes! ⚡ Sus pulsaciones percutoras trabajan por ti para brindarte una experiencia de masaje cómoda y práctica. Disfruta de tu masaje cuando quieras y donde quieras. ¡Consigue la tuya hoy!"
2. "¡Dale a tus músculos el descanso que merecen! 🔥 Con su diseño práctico y tecnología de percusión, disfrutar de un masaje nunca fue tan sencillo. Presiona y disfruta. ¡Haz tu pedido ahora!"
3. "¿Necesitas un momento de relajación? 💆 Conoce la pistola de masaje con mango largo que combina tecnología de percusión y potencia para ayudarte a relajar tus músculos. ✨ Mango largo y curvo. ✨ 4 cabezales. ✨ Masajes sin esfuerzo. ¡Pide la tuya hoy!"
4. Independencia: "Relájate sin depender de nadie 💆 Su mango largo y curvo llega a tu espalda y tus hombros sin que tengas que pedir ayuda. Elige entre 4 cabezales y date tu masaje cuando quieras. ✔ Envío gratis a todo México ✔ Garantía de 90 días ¡Pide la tuya hoy!" (usar solo como texto principal; esa frase ya no es titular de imagen).
5. Regalo: "El regalo práctico que sí van a usar 🎁 Pistola de masaje con mango largo, 4 cabezales y 2 colores para elegir. Llega a tu casa con rastreo, con envío gratis y 90 días de garantía. Pídela hoy para que llegue a tiempo para la Navidad. (Entrega estimada: 10 a 15 días hábiles.)"
6. Corto (Reels/Historias): "Tecnología que masajea por ti. Mango largo, 4 cabezales, envío gratis a todo México. ¡Pide la tuya!"
- **Descripciones:** "Envío gratis · Garantía de 90 días" / "Mango largo y curvo · 4 cabezales · USB-C" / "Negro o plateado · Atención por mensaje". **CTA:** "Comprar ahora" o "Ver más".

### Respuestas a objeciones (ficha y comentarios)
- ¿Cuánto tarda? Entre 10 y 15 días hábiles con número de rastreo; si no llega en ese plazo más 5 días hábiles, se investiga y se repone o se devuelve el dinero.
- ¿Y si falla? 90 días de garantía contra defectos de fabricación.
- ¿Se puede devolver? Revocación dentro de 5 días hábiles de recibido; si llega defectuosa o distinta, reposición o reembolso.
- ¿Cuánto dura la batería? Responder solo con el dato real de la muestra; mientras tanto: "Es recargable por USB-C".
- ¿Es seguro? Uso personal de relajación muscular, no sustituye atención médica; consultar al médico si hay embarazo, marcapasos o lesión; no usar sobre huesos, piel dañada o zonas inflamadas.

### Qué NO decir
"Intensidad ajustable" como promesa vaga (usar el dato confirmado de 9 niveles solo si Camila lo aprueba para anuncios), "99 velocidades", "horas de batería", "silencioso", "alivia el dolor", "elimina contracturas", "recomendado por médicos", "Oferta Buen Fin" si el precio no baja de verdad.

### Plan de prueba en Meta (propuesto, no ejecutado)
- 4 ángulos × 2 imágenes = 8 anuncios, presupuesto bajo y parejo, público amplio México 25 a 55+, sin segmentar por salud.
- Cortar el que gaste ~MX$350 sin compras; escalar solo si el costo por compra baja de ~MX$140 (la utilidad por venta es ~MX$277).
- Medir costo por compra, clics a la ficha y pagos iniciados.
- Antes de gastar: píxel de Meta, pedido real de prueba y confirmar stock del proveedor.
- Buen Fin 2026: 13 al 17 de noviembre. Black Friday: 27 de noviembre.

### Investigación de cliente y competencia (resumen; detalle y fuentes en `investigacion-cliente-competencia-copy.md`)
- Perfil A "persona que trabaja sentada" (25–45, oficina/home office): quiere terminar el día sin tensión en hombros y espalda. Perfil B "no llego a mi espalda" (35–65): quiere independencia; **es el que mejor encaja con el mango largo**. Perfil C "el que regala" (28–55): Navidad/Buen Fin, teme que llegue tarde o se vea barato. Todo esto es **inferencia**, no encuesta.
- Competencia directa de mango largo en Amazon México (8-nov-2026): pocos, con pocas reseñas y notas mixtas; los baratos desde MX$268 y los bien calificados MX$1,100–1,700 llegando de EE. UU. Marcas fuertes: RENPHO (~MX$1,393, 4.6★), Theragun Relief (MX$2,999). Hueco de la marca: calidad percibida alta, mango largo y garantía clara a MX$699.
- Barreras de compra: tienda nueva, entrega larga (Amazon promete 1–3 días), miedo a que falle la batería, comparación de precio. Respuesta: garantía 90 días, rastreo, datos reales de contacto, políticas visibles.
- Nota: en ese archivo hay sugerencias de titulares y textos más antiguas; **los titulares y textos aprobados son los de esta sección 8**.

### Página de Facebook y publicaciones
- Página "Nexthing" (id 61596214507976; facebook.com/profile.php?id=61596214507976). Categoría Shopping & retail. Sitio web: https://nexthingis.myshopify.com. Bio: "Lo siguiente que vas a querer, directo a tu puerta ⚡ Productos prácticos que trabajan por ti. Envío gratis a todo México · Garantía de 90 días · Rastreo de tu pedido".
- Foto de perfil: la N del logo. Portada: `logo/nexthing-portada-facebook-v2.jpg` (logo, "Descubre lo siguiente.", envío y garantía, centrada para PC y celular).
- Sin teléfono, correo, dirección ni WhatsApp. El correo de contacto de la página aún es camilacor0504@gmail.com (ofrecerle cambiarlo a nexthingsoporte@gmail.com).
- **4 posts orgánicos publicados** (sin impulsar, "Boost post" apagado, sin etiqueta de IA), imágenes en `imagenes-posts/`: 1) presentación de marca, 2) 4 cabezales, 3) negro o plateado + regalo navideño, 4) cómo se usa. No se aceptó el botón "Llamar ahora" de Facebook (no hay número comercial).
- Para publicar vía Chrome: usar `find` para obtener refs, `file_upload` al input de archivo, "Siguiente" → "Ajustes de publicación" (Boost apagado) → "Publicar"; rechazar "Llamar ahora" con "Ahora no".
- **Pendiente:** cuenta de anuncios, Business Manager y píxel de Meta.

---

## 9. OPERACIÓN DE PEDIDOS (guía vigente: `guia-cuando-llega-un-pedido.md`)

1. Llega el aviso de Shopify. 2. Revisar: pago "Pagado" (si "Pendiente" no comprar), producto y color, dirección completa con teléfono, riesgo de fraude. 3. Si falta un dato, escribir al cliente. 4. Comprar en DSers (Orders > Place order) y pagar en AliExpress (lo paga Camila); anotar el costo real. 5. Rastreo: el plan Basic debería sincronizarlo a Shopify; si al tercer día no aparece, copiarlo a mano en "Marcar como enviado" con notificar al cliente. 6. Seguimiento cada 2–3 días, respuesta en menos de 24 h; si pasan 20 días sin movimiento, disputa en AliExpress. 7. A los 5–7 días de la entrega, pedir reseña.
Problemas: cancelación antes/después de comprar, defecto (garantía 90 días), no llegó, arrepentimiento (5 días hábiles), contracargo (responder en Shopify con rastreo, conversación y política).
Antes del primer pedido: método de pago en DSers listo (~MX$350 por pedido), notificaciones de pedidos activas, revisar stock del proveedor (quedaban ~8).

---

## 10. NUEVOS PRODUCTOS: DECISIÓN VIGENTE E INVESTIGACIÓN

### Qué pidió Camila
Ampliar la tienda con productos de electrónica y accesorios tecnológicos rentables para México, vendidos con anuncios de Meta, de un nicho parecido al actual, simples (sin "electrónicos complicados"), con **precio fijo** (no productos en oferta, aunque finalmente aceptó estos dos), entrega ≤ 9 días y costo bajo.

### Criterios que usé
- Proveedor de AliExpress con **almacén en México** y envío gratis; entrega estimada **13–18 NOV** (4 a 9 días desde el 9-nov).
- Costo total (producto + envío) de hasta ~MX$130 a 230; valor percibido alto; problema visible en video corto; compra por impulso o regalo; sin riesgo de rechazo de Meta.
- Verificado en cada ficha: precio, ventana de entrega, % de entregas ≤ 8 días, devolución, stock, reseñas y calificación, tienda y seguidores.
- Cómo distinguir oferta de precio fijo en la ficha: aviso "Oferta por reserva anticipada, solo quedan N", "Máx. N uds./comprador a este precio" o "Termina: fecha".
- Demanda: Google Trends México (últimos 12 meses, valores relativos). Precios de competencia: Mercado Libre y Amazon México vía notas de Xataka y listados.
- **Suposiciones de utilidad:** comisión de Shopify Payments 3.6 % + MX$3; reserva de reembolsos 3 %; costo por compra en Meta MX$150–250 (**suposición mía, no medida**).

### DECISIÓN DE CAMILA: los dos productos
**1. Estación de carga inalámbrica 3 en 1 Mr. Gadgets 15W (celular, audífonos y reloj)**
- Enlace: https://es.aliexpress.com/item/1005013452940968.html
- Tienda: MR GADGETS MX Store (marca oficial), 87.5 % de valoraciones positivas, 3 seguidores. Más de 100,000 artículos similares vendidos.
- Costo: **MX$122.97** (precio normal de lista MX$685.44). Envío **MX$0** ("Envío gratis · Envío desde México"). Entrega **13–18 NOV (94.9 % en 8 días o menos)**. Devolución gratis 15 días; reembolso por pérdida, daño o si no llega en 30 días; cupón MX$20 por entrega tardía.
- Es **oferta de reserva anticipada**: "solo queda 1" y máximo 1 por comprador. El costo real hay que confirmarlo en DSers.
- Mercado: el mismo tipo de estación ronda MX$378 en Mercado Libre y MX$424–541 en Amazon México.

**2. Power bank inalámbrico MKTEL W10F 10,000 mAh**
- Enlace: https://es.aliexpress.com/item/1005013031575276.html
- Datos de la ficha: carga rápida 22.5 W, cable 2 en 1 Tipo-C + Lightning, diseño compacto portátil, color negro. 4.9★ con 15 reseñas; 85 ventas.
- Costo: **MX$133.16** (precio normal MX$532.66). Envío **MX$0**. Entrega **13–18 NOV (97.4 % en 8 días o menos)**. Máximo 3 piezas por comprador a ese precio (promoción).
- Mercado: power banks inalámbricas de 10,000 mAh en México ~MX$230–416.
- **Sin confirmar:** medidas, peso, potencia real de la carga inalámbrica, compatibilidad MagSafe. Pedir muestra (la pagaría Camila) antes de prometer algo.

**Demanda en Google Trends México (interés relativo):** "power bank" ≈ 73 (el más alto de todo lo comparado, con pico en diciembre), "cargador inalámbrico" ≈ 65–75 estable con picos en nov-dic, "cargador GaN" ≈ 30 y en alza. Como "cargador inalámbrico 3 en 1" casi no se busca así, los anuncios deben decir "carga todo en un solo lugar" y no el término técnico.

### Precios de venta decididos por Camila y utilidad
| Producto | Costo | Envío | Venta | Comisión + reserva | Utilidad bruta | Margen |
|---|---|---|---|---|---|---|
| Estación 3 en 1 | MX$122.97 | MX$0 | **MX$249** | MX$19.43 | **MX$106.60** | 42.8 % |
| Power bank | MX$133.16 | MX$0 | **MX$269** | MX$20.75 | **MX$115.09** | 42.8 % |
| Kit (ambos) | MX$256.13 | MX$0 | **MX$449** | MX$32.63 | **MX$160.24** | 35.7 % |

- El kit queda con precio de MX$449 (vs MX$518 por separado: 13 % de descuento). Cada producto se vende además por separado. Camila confirmó dejarlo en 449 (le sugerí MX$499, ≈MX$208 de utilidad, y lo rechazó).
- **Lo que debe tener claro:** con un costo por compra en Meta de MX$150, el resultado por pedido es -MX$43 (estación), -MX$35 (power bank) y +MX$10 (kit); con MX$250: -143, -135 y -90. Es rentable en bruto pero **no cubre un costo por compra típico de Meta**; solo el kit se acerca al equilibrio. Recomendación ya dada: empujar el kit como oferta principal y probar con poco dinero (MX$300–500) para medir el costo real por compra.
- **Riesgos de ambos:** costos de oferta que pueden subir (listas MX$685.44 y MX$532.66), poca prueba social, calidad no probada, Mr. Gadgets con 87.5 % de positivas, y que los anuncios en Meta aún no están probados.
- Ideas de anuncio (aún no escritas ni diseñadas): "Un solo lugar para cargar todo" (celular, reloj y audífonos se posan y se encienden) y "El regalo que no se espera" (versión navideña); no prometer "carga X veces tu celular" sin probar; imágenes sin personas reales.

### SIGUIENTE PASO (no ejecutado)
1. Camila inicia sesión en DSers (la sesión está cerrada).
2. Camila da su visto bueno expreso (por ejemplo "listo, agrégalos").
3. Entonces se agregan **solo esos dos productos** a la **lista de importación de DSers**, sin importar a Shopify ni publicar, para ver costo + envío reales en DSers. (Un intento de "Add To DSers" desde la ficha de AliExpress devolvió "Please refresh DSers web page and try again" porque DSers no tenía sesión.)
4. Después, preparar en borrador las fichas de producto y del kit (copy, imágenes sin personas reales, especificaciones verificadas, políticas coherentes) y publicar solo con autorización expresa.

---

## 11. PENDIENTES ABIERTOS

**De Camila**
- Terminar o quitar PayPal en el checkout.
- Dominio propio (lo compra ella).
- Cuenta de anuncios, Business Manager y píxel de Meta.
- Iniciar sesión en DSers y autorizar los dos productos nuevos.
- Cambiar el correo de contacto de la página de Facebook (opcional).
- Definir fecha de fin de la "súper oferta" o renombrarla.
- Pedir muestras (pistola y productos nuevos) y confirmar costo real, stock y tiempos con el primer pedido.
- Revisar la tienda en un celular real.
- Decidir si quiere el logo en pie de página, checkout y correos.
- WhatsApp comercial (no existe todavía).

**Para Claude (con autorización de Camila)**
- Reordenar la galería de la pistola; cambiar "YouTube URL" en Judge.me.
- Mejorar el pequeño parpadeo inicial de la portada móvil con una clase en `<head>` (por ejemplo `html.nx-hold`).
- Cuando haya varios productos, revisar que los textos de la tienda no hablen solo del masajeador.
- Borrar el cliente de prueba "PRUEBA Camila" (opcional).
- Datos sin confirmar de la pistola: autonomía, peso, ruido, dimensiones.

---

## 12. MAPA DE ARCHIVOS (carpeta `Dropshipping`)

- `HANDOFF-NEXTHING.md` — este documento (fuente de verdad).
- `investigacion-cliente-competencia-copy.md` — cliente ideal, motivos de compra, competencia, reglas de Meta, plan de prueba y fuentes.
- `politicas-nexthing.md` — texto de políticas (privacidad y términos completos).
- `guia-cuando-llega-un-pedido.md` — operación de pedidos.
- `mensajes-para-pedir-resenas.md` — mensajes para reseñas reales.
- `anuncios-meta/` — 3 diseños finales × 3 formatos.
- `imagenes-tienda/` — galería del producto (`1-cabezales`, `2-mango-controles`, `3-mango-largo`, `4-colores`, `5-especificaciones`, `6-lo-que-incluye`, `7-como-se-usa`), heroes de marca PC/móvil y recortes `nx-pistola-negra.png` / `nx-pistola-plata.png`.
- `imagenes-posts/` — 4 imágenes de los posts de Facebook.
- `logo/` — logos, íconos, favicon, perfil y portada de Facebook.
- `fotos-pistola/` — fotos del proveedor (sin personas).
- `scripts-generadores/` — scripts de Node y fuentes para generar imágenes (se necesita `npm install`; dependencias en `package.json`).
- Memoria de Claude (reglas y criterios): `memoria-claude/` dentro del zip (en el equipo: `C:\Users\Corral\.claude\projects\C--Users-Corral--claude-projects-Dropshipping\memory\`).

---

## 13. CÓMO TRABAJAR CON LAS HERRAMIENTAS (notas operativas vigentes)

- **Chrome:** abrir pestañas nuevas, usar `browser_batch` para varias acciones por llamada y cerrar las que se abran. Las pestañas de Shopify admin y Facebook se traban a veces: abrir una nueva y esperar.
- **Editor de código del tema:** buscar/reemplazar con ctrl+h y reemplazar todo con ctrl+alt+Enter, en modo literal (el modo regex congela la pestaña; se alterna con alt+r). Confirmar "1 of 1" coincidencias antes de reemplazar. El historial (Timeline) permite restaurar versiones. Para cambiar el orden de secciones o imágenes del hero, editar `templates/index.json` (arrastrar no funciona bien). El CSS personalizado de una sección permite 500 caracteres.
- **Políticas y descripciones (TinyMCE):** en la página de admin usar `window.tinymce.activeEditor.getContent()` / `setContent()` y luego "Guardar".
- **Datos de la tienda en vivo:** `/products/<handle>.js` (Shopify lo cachea: agregar un query string distinto) y `/policies/<nombre>`.
- **AliExpress (solo lectura):** ficha `https://es.aliexpress.com/item/<ID>.html`; búsqueda `https://es.aliexpress.com/w/wholesale-<slug>.html?shipFromCountry=MX&SearchText=...&maxPrice=...&sortType=total_tranpro_desc`. Los datos se leen del DOM (`document.body.innerText`); la descripción larga está en un shadow DOM (`element.shadowRoot.textContent`). `fetch` devuelve vacío (se renderiza en cliente). Si la herramienta muestra "[BLOCKED: Cookie/query string data]", quitar `= & ?` y URLs del texto extraído.
- **Google Trends:** `https://trends.google.com/trends/explore?geo=MX&date=today%2012-m&q=<t1>,<t2>,...` (hasta 5 términos; valores relativos entre sí; "0" significa muy por debajo del término más buscado).
- **Imágenes:** los scripts en `scripts-generadores/` generan los anuncios y posts con fuentes incluidas.
- No agregar atribución de IA a los contenidos de la tienda o de Facebook por indicación de Camila.
