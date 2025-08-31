<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tutorial Interactivo de Normalización de Base de Datos</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <style>
        body {
            background-image: url('4FN.png');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            background-color: transparent;
            padding: 40px 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            color: #ffffff;
        }
        .container {
            max-width: 1200px;
            background-color: transparent;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
        }
        .card-header {
            background-color: #2a2a72;
            color: white;
        }
        .btn-link {
            color: white;
            text-decoration: none;
        }
        .btn-link:hover {
            color: #93c5fd;
            text-decoration: underline;
        }
        .table th {
            background-color: #4b5e9b;
        }
        .lead {
            font-size: 1.5rem;
            font-weight: bold;
            color: #1e3a8a;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
        }
        .name-highlight {
            color: #1e3a8a;
            font-weight: bold;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.2);
            background-color: rgba(147, 197, 253, 0.2);
            padding: 2px 6px;
            border-radius: 5px;
        }
        .image-container {
            text-align: center;
            margin: 20px 0;
        }
        .image-container img {
            max-width: 100%;
            height: auto;
            border: 2px solid #93c5fd;
            border-radius: 10px;
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease, opacity 0.5s ease;
            opacity: 0.9;
        }
        .image-container img:hover {
            transform: scale(1.05);
            opacity: 1;
        }
        .btn-primary {
            background-color: #2a2a72;
            border-color: #2a2a72;
            border-radius: 20px;
            padding: 10px 20px;
            color: #ffffff;
            transition: background-color 0.3s, transform 0.3s;
        }
        .btn-primary:hover {
            background-color: #1e3a8a;
            border-color: #1e3a8a;
            transform: translateY(-3px);
        }
        .card-body {
            background-color: transparent;
            border-radius: 0 0 10px 10px;
            padding: 20px;
            color: #1e3a8a;
        }
        h1, h4, h5 {
            color: #1e3a8a;
            font-weight: bold;
            text-shadow: 1px 1px 4px rgba(0, 0, 0, 0.4);
        }
        ul {
            list-style-type: "⭐ ";
            padding-left: 30px;
            color: #1e3a8a;
        }
        .fun-note {
            font-style: italic;
            color: #ffffff;
            margin-top: 10px;
        }
        ul strong {
            color: #1e3a8a;
            font-weight: 800;
        }
        .fade-in {
            animation: fadeIn 1s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 class="text-center mb-4">Tutorial Interactivo de Normalización de Base de Datos</h1>
        <p class="lead text-center mb-5">¡Descubre cómo organizar datos como un experto! Esta página, creada por <span class="name-highlight">Juan Esteban Catalán Sánchez</span>, te enseña las formas normales (1FN, 2FN, 3FN) con ejemplos divertidos de una tienda de zapatos y cómo implementarlas en MySQL. ¡Explora, aprende y juega con los detalles!</p>

        <!-- Sección MySQL -->
        <div class="accordion mb-4 fade-in" id="mysqlAccordion">
            <div class="card">
                <div class="card-header" id="headingCode">
                    <h2 class="mb-0">
                        <button class="btn btn-link btn-block text-left" type="button" data-toggle="collapse" data-target="#collapseCode" aria-expanded="true" aria-controls="collapseCode">
                            <strong>💻 Código en MySQL</strong>
                        </button>
                    </h2>
                </div>
                <div id="collapseCode" class="collapse show" aria-labelledby="headingCode" data-parent="#mysqlAccordion">
                    <div class="card-body">
                        <div class="accordion" id="subAccordion">
                            <!-- Creación -->
                            <div class="card">
                                <div class="card-header" id="headingCreate">
                                    <h2 class="mb-0">
                                        <button class="btn btn-link btn-block text-left collapsed" type="button" data-toggle="collapse" data-target="#collapseCreate" aria-expanded="false" aria-controls="collapseCreate">
                                            ⚙️ Creación
                                        </button>
                                    </h2>
                                </div>
                                <div id="collapseCreate" class="collapse" aria-labelledby="headingCreate" data-parent="#subAccordion">
                                    <div class="card-body">
                                        <p>📌 <strong>Creación (Base de datos y tablas)</strong></p>
                                        <p>Cuando hablamos de <strong>crear una base de datos</strong>, nos referimos a diseñar un lugar donde se va a guardar la información de manera organizada.</p>
                                        <p>Piensa en la base de datos como una <strong>biblioteca 📚</strong>:</p>
                                        <ul>
                                            <li>La base de datos es toda la <strong>biblioteca completa</strong>.</li>
                                            <li>Las tablas son como las <strong>estanterías</strong>, cada una con un tema específico (clientes, productos, ventas, etc.).</li>
                                            <li>Cada columna es como una <strong>categoría</strong> en esa estantería (nombre, edad, precio, cantidad, etc.).</li>
                                            <li>Cada fila es un <strong>registro</strong>, como un libro que guarda la información detallada.</li>
                                        </ul>
                                        <p>La <strong>creación</strong> es importante porque define la estructura que tendrá tu información. Si no se diseña bien desde el inicio, después puede ser difícil mantener los datos en orden.</p>
                                        <div class="image-container">
                                            <img src="creacion1.PNG" alt="Creación de tabla parte 1">
                                        </div>
                                        <div class="image-container">
                                            <img src="creacion2.PNG" alt="Creación de tabla parte 2">
                                        </div>
                                        <div class="image-container">
                                            <img src="creacion3.PNG" alt="Creación de tabla parte 3">
                                        </div>
                                        <div class="image-container">
                                            <img src="creacion4.PNG" alt="Creación de tabla parte 4">
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <!-- Insertar -->
                            <div class="card">
                                <div class="card-header" id="headingInsert">
                                    <h2 class="mb-0">
                                        <button class="btn btn-link btn-block text-left collapsed" type="button" data-toggle="collapse" data-target="#collapseInsert" aria-expanded="false" aria-controls="collapseInsert">
                                            📝 Insertar
                                        </button>
                                    </h2>
                                </div>
                                <div id="collapseInsert" class="collapse" aria-labelledby="headingInsert" data-parent="#subAccordion">
                                    <div class="card-body">
                                        <p>📌 <strong>Inserción (Agregar datos a la base de datos)</strong></p>
                                        <p>Una vez que tienes las estanterías listas (las tablas), necesitas <strong>llenarlas con información</strong>, es decir, insertar los datos.</p>
                                        <p>Por ejemplo: en la tabla <strong>Clientes</strong>, insertas nombres, teléfonos y direcciones; en <strong>Productos</strong>, guardas precios, cantidades y descripciones.</p>
                                        <h5>👉 ¿Por qué es importante insertar los datos?</h5>
                                        <ul>
                                            <li>Porque la base de datos por sí sola está vacía, como una <strong>estantería sin libros</strong>.</li>
                                            <li>Insertar datos permite analizar la información, hacer consultas y obtener resultados (ejemplo: "¿Cuál es el producto más vendido?" o "¿Quién gastó más dinero?").</li>
                                            <li>También garantiza que la información esté disponible y centralizada, evitando que se pierda o quede regada en documentos sueltos.</li>
                                        </ul>
                                        <div class="image-container">
                                            <img src="insertar.PNG" alt="Ejemplo de inserción en MySQL">
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <!-- Consultas -->
                            <div class="card">
                                <div class="card-header" id="headingConsultas">
                                    <h2 class="mb-0">
                                        <button class="btn btn-link btn-block text-left collapsed" type="button" data-toggle="collapse" data-target="#collapseConsultas" aria-expanded="false" aria-controls="collapseConsultas">
                                            📊 Consultas
                                        </button>
                                    </h2>
                                </div>
                                <div id="collapseConsultas" class="collapse" aria-labelledby="headingConsultas" data-parent="#subAccordion">
                                    <div class="card-body">
                                        <div class="accordion" id="consultasAccordion">
                                            <!-- Consultas Simples -->
                                            <div class="card">
                                                <div class="card-header" id="headingSimple">
                                                    <h2 class="mb-0">
                                                        <button class="btn btn-link btn-block text-left collapsed" type="button" data-toggle="collapse" data-target="#collapseSimple" aria-expanded="false" aria-controls="collapseSimple">
                                                            🔹 Consultas Simples
                                                        </button>
                                                    </h2>
                                                </div>
                                                <div id="collapseSimple" class="collapse" aria-labelledby="headingSimple" data-parent="#consultasAccordion">
                                                    <div class="card-body">
                                                        <div class="image-container">
                                                            <img src="consulta_simple1.PNG" alt="Consulta Simple 1">
                                                        </div>
                                                        <div class="image-container">
                                                            <img src="consulta_simple2.PNG" alt="Consulta Simple 2">
                                                        </div>
                                                        <div class="image-container">
                                                            <img src="consulta_simple3.PNG" alt="Consulta Simple 3">
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                            <!-- Consultas Intermedias -->
                                            <div class="card">
                                                <div class="card-header" id="headingIntermedia">
                                                    <h2 class="mb-0">
                                                        <button class="btn btn-link btn-block text-left collapsed" type="button" data-toggle="collapse" data-target="#collapseIntermedia" aria-expanded="false" aria-controls="collapseIntermedia">
                                                            🔹 Consultas Intermedias
                                                        </button>
                                                    </h2>
                                                </div>
                                                <div id="collapseIntermedia" class="collapse" aria-labelledby="headingIntermedia" data-parent="#consultasAccordion">
                                                    <div class="card-body">
                                                        <div class="image-container">
                                                            <img src="consulta_intermedia1.PNG" alt="Consulta Intermedia 1">
                                                        </div>
                                                        <div class="image-container">
                                                            <img src="consulta_intermedia2.PNG" alt="Consulta Intermedia 2">
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                            <!-- Consultas Avanzadas -->
                                            <div class="card">
                                                <div class="card-header" id="headingAvanzada">
                                                    <h2 class="mb-0">
                                                        <button class="btn btn-link btn-block text-left collapsed" type="button" data-toggle="collapse" data-target="#collapseAvanzada" aria-expanded="false" aria-controls="collapseAvanzada">
                                                            🔹 Consultas Avanzadas
                                                        </button>
                                                    </h2>
                                                </div>
                                                <div id="collapseAvanzada" class="collapse" aria-labelledby="headingAvanzada" data-parent="#consultasAccordion">
                                                    <div class="card-body">
                                                        <div class="image-container">
                                                            <img src="consulta_avanzada1.PNG" alt="Consulta Avanzada 1">
                                                        </div>
                                                        <div class="image-container">
                                                            <img src="consulta_avanzada2.PNG" alt="Consulta Avanzada 2">
                                                        </div>
                                                        <div class="image-container">
                                                            <img src="consulta_avanzada3.PNG" alt="Consulta Avanzada 3">
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <!-- Extras -->
                            <div class="card">
                                <div class="card-header" id="headingExtras">
                                    <h2 class="mb-0">
                                        <button class="btn btn-link btn-block text-left collapsed" type="button" data-toggle="collapse" data-target="#collapseExtras" aria-expanded="false" aria-controls="collapseExtras">
                                            🌟 Extras
                                        </button>
                                    </h2>
                                </div>
                                <div id="collapseExtras" class="collapse" aria-labelledby="headingExtras" data-parent="#subAccordion">
                                    <div class="card-body">
                                        <p>📌 <strong>Recursos extras para reforzar el aprendizaje</strong></p>
                                        <div class="image-container">
                                            <img src="extra1.PNG" alt="Extra 1">
                                        </div>
                                        <div class="image-container">
                                            <img src="extra2.PNG" alt="Extra 2">
                                        </div>
                                        <div class="image-container">
                                            <img src="extra3.PNG" alt="Extra 3">
                                        </div>
                                        <div class="image-container">
                                            <img src="extra4.PNG" alt="Extra 4">
                                        </div>
                                        <div class="image-container">
                                            <img src="extra5.PNG" alt="Extra 5">
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Sección Normalización -->
        <div class="accordion" id="normalizationAccordion">
            <!-- 1FN -->
            <div class="card mb-3">
                <div class="card-header" id="headingOne">
                    <h2 class="mb-0">
                        <button class="btn btn-link btn-block text-left" type="button" data-toggle="collapse" data-target="#collapseOne" aria-expanded="true" aria-controls="collapseOne">
                            <strong>Primera Forma Normal (1FN): El Primer Paso para Organizar</strong>
                        </button>
                    </h2>
                </div>
                <div id="collapseOne" class="collapse show" aria-labelledby="headingOne" data-parent="#normalizationAccordion">
                    <div class="card-body">
                        <p>Imagina que tienes una lista de compras en una hoja de papel donde todo está escrito en una sola columna larga: nombres de clientes, fechas, productos, precios... todo mezclado. Esto es como una base de datos sin normalizar. La Primera Forma Normal (1FN) es como dividir esa lista en columnas separadas en una tabla, asegurándonos de que cada celda contenga solo un valor simple y único, sin listas o grupos repetidos dentro de una misma celda. Por ejemplo, en lugar de poner "Juan Pérez, 25 años, Bogotá" en una sola celda, lo dividimos en columnas separadas para nombre, edad y ciudad. Esto hace que la información sea "atómica", es decir, indivisible, como átomos en la química.</p>
                        <p>En nuestra base de datos de ventas de zapatos, empezamos con una tabla grande que incluye todo: detalles de la venta, el cliente, el producto, la tienda y la fecha. Aunque esto parece simple al principio, causa problemas como repetir la misma información muchas veces (por ejemplo, si un cliente compra varios zapatos, su nombre y edad se escriben una y otra vez). Esto no solo ocupa más espacio, sino que puede llevar a errores: ¿qué pasa si actualizas la edad de un cliente en una fila pero olvidas las demás? ¡Inconsistencias por todos lados!</p>
                        <h4><strong>¿Qué se realizó exactamente en la 1FN?</strong></h4>
                        <p>El objetivo principal fue eliminar cualquier valor multivaluado. Si una celda tenía varios datos separados por comas (como "zapatos, botas, tenis"), lo convertimos en filas separadas o columnas individuales. En este caso, la tabla ya estaba cerca de la 1FN, pero aseguramos que cada columna represente un solo atributo. Sin embargo, todavía hay redundancias porque la información no está separada en temas lógicos. Esto resuelve problemas básicos de almacenamiento, pero deja anomalías: no puedes agregar un cliente nuevo sin una venta, y eliminar una venta podría borrar datos importantes del cliente.</p>
                        <div class="image-container">
                            <img src="1FN.png" alt="Diagrama de la Primera Forma Normal (1FN)">
                        </div>
                        <p>En la imagen arriba, ves cómo se ve la estructura inicial. ¡Pásale el mouse para un efecto sorpresa!</p>
                        <button class="btn btn-primary" data-toggle="collapse" data-target="#details1FN">Explorar Detalles Interactivos y Más Explicaciones</button>
                        <div id="details1FN" class="collapse mt-3">
                            <ul>
                                <li><strong>Por qué es importante:</strong> Sin 1FN, buscar información es como buscar tu calcetín perdido en un cajón caótico. ¡Con ella, todo fluye fácil!</li>
                                <li><strong>Anomalía de Inserción:</strong> No puedes agregar un amigo que aún no ha comprado. ¡Es como no invitar a alguien a una fiesta sin un regalo primero!</li>
                                <li><strong>Anomalía de Actualización:</strong> Si tu amigo se muda, debes actualizar su dirección en todas las listas. ¡Olvida una y tendrás un misterio de ciudades!</li>
                                <li><strong>Anomalía de Eliminación:</strong> Borras una compra y ¡boom!, adiós datos del cliente. ¡Es como perder un capítulo de tu serie favorita!</li>
                                <li><strong>Truco divertido:</strong> Imagina que eres un superhéroe organizando datos. ¡La 1FN es tu capa inicial!</li>
                                <li><strong>Desafío para ti:</strong> Prueba dividir una lista desordenada en columnas. ¿Cuántos errores evitas?</li>
                                <li><strong>Extra de diversión:</strong> ¡Gana puntos imaginarios cada vez que entiendas una anomalía!</li>
                            </ul>
                            <p class="fun-note">¡Sigue explorando y diviértete aprendiendo a ser un maestro de datos!</p>
                        </div>
                    </div>
                </div>
            </div>
            <!-- 2FN -->
            <div class="card mb-3">
                <div class="card-header" id="headingTwo">
                    <h2 class="mb-0">
                        <button class="btn btn-link btn-block text-left collapsed" type="button" data-toggle="collapse" data-target="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">
                            <strong>Segunda Forma Normal (2FN): Eliminando Repeticiones Parciales</strong>
                        </button>
                    </h2>
                </div>
                <div id="collapseTwo" class="collapse" aria-labelledby="headingTwo" data-parent="#normalizationAccordion">
                    <div class="card-body">
                        <p>Ahora que tenemos nuestra tabla organizada en columnas simples (gracias a la 1FN), notamos que hay repeticiones. Por ejemplo, si el mismo zapato se vende muchas veces, su precio y descripción se repiten en cada fila. La Segunda Forma Normal (2FN) resuelve esto separando la información en tablas más pequeñas y especializadas. Cada tabla se enfoca en un tema: una para clientes, otra para productos, otra para fechas, etc. Usamos "claves" (como números ID únicos) para conectarlas, como hilos que unen piezas de un rompecabezas.</p>
                        <p>En términos simples, 2FN asegura que cada pieza de información dependa completamente de la "clave principal" de su tabla. Si algo depende solo de parte de la clave (en tablas con claves compuestas), lo movemos a una nueva tabla. En nuestra tienda de zapatos, creamos tablas separadas para "Tiempo" (fechas), "Cliente", "Producto", "Tienda" y "Venta" (que une todo). Así, el nombre de un cliente se guarda solo una vez, y en la tabla de ventas solo ponemos su ID. Esto reduce el espacio y evita errores al actualizar datos.</p>
                        <h4><strong>¿Qué se realizó exactamente en la 2FN?</strong></h4>
                        <p>Identificamos "dependencias parciales": por ejemplo, la edad de un cliente depende solo del cliente, no de la venta específica. Así que movimos esos detalles a su propia tabla. Ahora, si un producto cambia de precio, lo actualizas en un solo lugar. Esto hace la base más eficiente, como organizar tus fotos en álbumes temáticos en lugar de mezclar todo en una caja grande. Sin embargo, aún hay dependencias "transitivas" (como un campo que depende de otro campo no clave), que resolveremos en la siguiente forma.</p>
                        <p><strong>Estructura en 2FN (Esquema con Tablas Separadas):</strong> Aquí mostramos los campos de cada tabla para que veas cómo se divide la info.</p>
                        <p><strong>Tabla TIEMPO:</strong></p>
                        <table class="table table-bordered table-striped">
                            <thead><tr><th>Campo</th><th>Tipo</th></tr></thead>
                            <tbody>
                                <tr><td>Id_Fecha</td><td>INT (PK)</td></tr>
                                <tr><td>Fecha</td><td>DATE</td></tr>
                                <tr><td>Año</td><td>INT</td></tr>
                                <tr><td>Mes</td><td>INT</td></tr>
                                <tr><td>Trimestre</td><td>INT</td></tr>
                                <tr><td>Dia_Nombre</td><td>VARCHAR</td></tr>
                            </tbody>
                        </table>
                        <p><strong>Tabla CLIENTE:</strong></p>
                        <table class="table table-bordered table-striped">
                            <thead><tr><th>Campo</th><th>Tipo</th></tr></thead>
                            <tbody>
                                <tr><td>Id_Cliente</td><td>INT (PK)</td></tr>
                                <tr><td>Nombre</td><td>VARCHAR</td></tr>
                                <tr><td>Genero</td><td>VARCHAR</td></tr>
                                <tr><td>Edad</td><td>INT</td></tr>
                                <tr><td>Ciudad</td><td>VARCHAR</td></tr>
                                <tr><td>Segmento</td><td>VARCHAR</td></tr>
                            </tbody>
                        </table>
                        <p><strong>Tabla PRODUCTO:</strong></p>
                        <table class="table table-bordered table-striped">
                            <thead><tr><th>Campo</th><th>Tipo</th></tr></thead>
                            <tbody>
                                <tr><td>Id_Producto</td><td>INT (PK)</td></tr>
                                <tr><td>Nombre_Producto</td><td>VARCHAR</td></tr>
                                <tr><td>Categoria</td><td>VARCHAR</td></tr>
                                <tr><td>Talla</td><td>VARCHAR</td></tr>
                                <tr><td>Genero</td><td>VARCHAR</td></tr>
                                <tr><td>Precio_Referencia</td><td>DECIMAL</td></tr>
                            </tbody>
                        </table>
                        <p><strong>Tabla TIENDA:</strong></p>
                        <table class="table table-bordered table-striped">
                            <thead><tr><th>Campo</th><th>Tipo</th></tr></thead>
                            <tbody>
                                <tr><td>Id_Tienda</td><td>INT (PK)</td></tr>
                                <tr><td>Nombre_Tienda</td><td>VARCHAR</td></tr>
                                <tr><td>Ciudad</td><td>VARCHAR</td></tr>
                                <tr><td>Tipo_Tienda</td><td>VARCHAR</td></tr>
                            </tbody>
                        </table>
                        <p><strong>Tabla VENTA:</strong></p>
                        <table class="table table-bordered table-striped">
                            <thead><tr><th>Campo</th><th>Tipo</th></tr></thead>
                            <tbody>
                                <tr><td>Id_Venta</td><td>INT (PK)</td></tr>
                                <tr><td>Id_Fecha</td><td>INT (FK)</td></tr>
                                <tr><td>Id_Producto</td><td>INT (FK)</td></tr>
                                <tr><td>Id_Cliente</td><td>INT (FK)</td></tr>
                                <tr><td>Id_Tienda</td><td>INT (FK)</td></tr>
                                <tr><td>Cantidad_Vendida</td><td>INT</td></tr>
                                <tr><td>Precio_unitario</td><td>DECIMAL</td></tr>
                                <tr><td>Total_Venta</td><td>DECIMAL</td></tr>
                            </tbody>
                        </table>
                        <div class="image-container">
                            <img src="2FN.png" alt="Diagrama de la Segunda Forma Normal (2FN)">
                        </div>
                        <p>La imagen muestra cómo las tablas se conectan con flechas, representando relaciones. ¡Pásale el mouse para un efecto mágico!</p>
                        <button class="btn btn-primary" data-toggle="collapse" data-target="#details2FN">Explorar Detalles Interactivos y Más Explicaciones</button>
                        <div id="details2FN" class="collapse mt-3">
                            <ul>
                                <li><strong>Dependencias Parciales Eliminadas:</strong> Si un precio depende solo del producto, ¡lo movemos a su casa (tabla)! Todo debe depender de la clave principal.</li>
                                <li><strong>Beneficios en la vida real:</strong> Más espacio libre y consultas rápidas. ¡Es como tener un armario organizado para encontrar tus zapatitos!</li>
                                <li><strong>Interactividad en bases de datos:</strong> Usa "JOIN" como un hechizo para unir tablas y ver todo como un mapa del tesoro.</li>
                                <li><strong>Problemas pendientes:</strong> "Trimestre" depende de "Mes", ¡es un pequeño misterio que resolveremos después!</li>
                                <li><strong>Truco divertido:</strong> Imagina que eres un chef separando ingredientes. ¡Cada tabla es una receta diferente!</li>
                                <li><strong>Desafío para ti:</strong> Intenta conectar dos tablas con un ID. ¡Siente el poder de la organización!</li>
                                <li><strong>Extra de diversión:</strong> ¡Gana una medalla virtual por cada tabla que entiendas!</li>
                            </ul>
                            <p class="fun-note">¡Sigue jugando y conviértete en un ninja de las bases de datos!</p>
                        </div>
                    </div>
                </div>
            </div>
            <!-- 3FN -->
            <div class="card mb-3">
                <div class="card-header" id="headingThree">
                    <h2 class="mb-0">
                        <button class="btn btn-link btn-block text-left collapsed" type="button" data-toggle="collapse" data-target="#collapseThree" aria-expanded="false" aria-controls="collapseThree">
                            <strong>Tercera Forma Normal (3FN): Limpiando Dependencias Escondidas</strong>
                        </button>
                    </h2>
                </div>
                <div id="collapseThree" class="collapse" aria-labelledby="headingThree" data-parent="#normalizationAccordion">
                    <div class="card-body">
                        <p>Con las tablas separadas en 2FN, todo parece mejor, pero aún hay "dependencias ocultas". Por ejemplo, en la tabla de Tiempo, el "Trimestre" se calcula directamente del "Mes" (enero-marzo es trimestre 1), no de la clave principal. Esto es una dependencia transitiva: A depende de B, y B depende de C, así que A depende indirectamente de C. La Tercera Forma Normal (3FN) elimina estas dependencias moviendo campos derivados a tablas nuevas o eliminándolos si se pueden calcular en el momento.</p>
                        <p>En simple: 3FN asegura que cada campo en una tabla dependa solo de la clave principal, no de otros campos no clave. Esto hace la base aún más limpia y evita anomalías. En nuestra base de ventas, revisamos cada tabla y removemos campos como "Trimestre" o "Día de la Semana", porque se pueden obtener automáticamente de la fecha usando fórmulas. Así, la base es más ligera y consistente: si cambias un mes, no tienes to preocuparte por actualizar el trimestre manualmente.</p>
                        <h4><strong>¿Qué se realizó exactamente en la 3FN?</strong></h4>
                        <p>Analizamos dependencias transitivas y las resolvimos. Por ejemplo, en la tabla TIEMPO, eliminamos "Trimestre" (calculable como (Mes-1)/3 +1) y "Dia_Nombre" (obtenible con funciones de fecha). Campos como "Total_Venta" en VENTA podrían calcularse (Cantidad * Precio), pero a veces se mantienen por velocidad en sistemas grandes. Esto optimiza el almacenamiento y previene errores, como tener un mes de febrero en trimestre 2 por un descuido.</p>
                        <p><strong>Estructura en 3FN (Esquema Optimizado):</strong> Nota cómo algunas tablas se simplifican.</p>
                        <p><strong>Tabla TIEMPO (Modificada para eliminar transitivas):</strong></p>
                        <table class="table table-bordered table-striped">
                            <thead><tr><th>Campo</th><th>Tipo</th></tr></thead>
                            <tbody>
                                <tr><td>Id_Fecha</td><td>INT (PK)</td></tr>
                                <tr><td>Fecha</td><td>DATE</td></tr>
                                <tr><td>Año</td><td>INT</td></tr>
                                <tr><td>Mes</td><td>INT</td></tr>
                            </tbody>
                        </table>
                        <p>Las otras tablas (CLIENTE, PRODUCTO, TIENDA, VENTA) se mantienen similares a 2FN, ya que no tenían más transitivas evidentes.</p>
                        <div class="image-container">
                            <img src="3FN.png" alt="Diagrama de la Tercera Forma Normal (3FN)">
                        </div>
                        <p>La imagen ilustra la estructura final, más limpia y conectada. ¡Pásale el mouse para un toque mágico!</p>
                        <button class="btn btn-primary" data-toggle="collapse" data-target="#details3FN">Explorar Detalles Interactivos y Más Explicaciones</button>
                        <div id="details3FN" class="collapse mt-3">
                            <ul>
                                <li><strong>Dependencias Transitivas Eliminadas:</strong> Quitamos los "atajos" como "Trimestre" para que todo dependa de la clave principal. ¡Sin trampas!</li>
                                <li><strong>Beneficios en la vida real:</strong> Menos errores y más espacio. ¡Es como limpiar tu mochila para un viaje épico!</li>
                                <li><strong>Interactividad en consultas:</strong> Usa QUARTER(Fecha) como un hechizo para calcular trimestres al instante.</li>
                                <li><strong>Notas finales para principiantes:</strong> 3FN es tu escudo dorado; hay niveles más altos, pero ¡ya eres un héroe de datos!</li>
                                <li><strong>Truco divertido:</strong> Imagina que eres un detective eliminando pistas falsas. ¡Solo queda la verdad!</li>
                                <li><strong>Desafío para ti:</strong> Calcula un trimestre con una fecha. ¡Eres el mago de los números!</li>
                                <li><strong>Extra de diversión:</strong> ¡Gana un trofeo virtual por dominar la 3FN!</li>
                            </ul>
                            <p class="fun-note">¡Sigue la aventura y sé el rey de la organización de datos!</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.3/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
</body>
</html>
