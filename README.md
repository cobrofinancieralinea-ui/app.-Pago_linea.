<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>FinaNova</title>

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600&display=swap" rel="stylesheet">

<style>
body {
    margin: 0;
    font-family: 'Inter', sans-serif;
    background: #0b1f1a;
}

/* APP */
.app {
    width: 100%;
    max-width: 420px;
    margin: auto;
    background: #0f2a24;
    min-height: 100vh;
}

/* HEADER */
.header {
    background: linear-gradient(135deg, #065f46, #0f766e);
    padding: 20px;
    color: white;
}

.header h2 {
    margin: 0;
}

.info {
    font-size: 13px;
    margin-top: 5px;
}

/* CARD PRINCIPAL */
.card {
    background: #12332c;
    margin: 15px;
    border-radius: 14px;
    padding: 18px;
}

.card-header {
    display: flex;
    justify-content: space-between;
}

/* TEXTO BLANCO SOLO DONDE PEDISTE */
.white {
    color: #ffffff !important;
}

.amount {
    font-size: 28px;
    margin: 10px 0;
}

/* BOTÓN */
.button {
    margin: 15px;
    background: linear-gradient(135deg, #10b981, #059669);
    text-align: center;
    padding: 14px;
    border-radius: 12px;
    font-weight: 600;
    color: white;
    cursor: pointer;
    transition: 0.2s;
}

.button:hover {
    transform: scale(1.02);
}

/* SECCIONES */
.section {
    margin: 15px;
}

.section-title {
    font-size: 13px;
    color: #6ee7b7;
    margin-bottom: 8px;
}

.small-card {
    background: #12332c;
    border-radius: 12px;
    padding: 12px;
    margin-bottom: 10px;
    font-size: 13px;
    color: #d1fae5;
    display: flex;
    justify-content: space-between;
}

/* INFO EXTRA */
.info-box {
    background: #064e3b;
    margin: 15px;
    padding: 12px;
    border-radius: 10px;
    font-size: 12px;
    color: #a7f3d0;
}

/* MODAL */
.modal {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.7);
    display: none;
    justify-content: center;
    align-items: center;
}

.modal-content {
    background: #0f2a24;
    padding: 25px;
    border-radius: 14px;
    text-align: center;
    width: 80%;
    max-width: 300px;
    color: white;
}

/* SPINNER */
.spinner {
    border: 4px solid rgba(255,255,255,0.1);
    border-top: 4px solid #10b981;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    margin: 0 auto 15px;
    animation: spin 1s linear infinite;
}

@keyframes spin {
    100% { transform: rotate(360deg); }
}

/* BOTÓN CERRAR */
.close-btn {
    margin-top: 15px;
    background: #059669;
    padding: 10px;
    border-radius: 8px;
    cursor: pointer;
}

/* RESPONSIVE */
@media (min-width: 768px) {
    body {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }

    .app {
        border-radius: 18px;
        box-shadow: 0 20px 60px rgba(0,0,0,0.6);
    }
}
</style>
</head>

<body>

<div class="app">

    <!-- HEADER -->
    <div class="header">
        <h2>FinaNova</h2>
        <div class="info">+54*****193</div>
        <div class="info">Lorena Itati Altamirano</div>
    </div>

    <!-- TARJETA PRINCIPAL -->
    <div class="card">
        <div class="card-header">
            <span class="white">Vence hoy</span>
            <span class="white">17/04/2026</span>
        </div>

        <div class="amount white">$81.000</div>

        <div style="font-size:13px; color:#a7f3d0;">
            Total a pagar de tu cuota actual.
        </div>
    </div>

    <!-- BOTÓN -->
    <div class="button" onclick="simularPago()">
        PAGAR AHORA
    </div>

    <!-- RESUMEN -->
    <div class="section">
        <div class="section-title">Resumen del crédito</div>

        <div class="small-card">
            <span>Cuotas pagadas</span>
            <span>0/1</span>
        </div>

        <div class="small-card">
            <span>Saldo pendiente</span>
            <span>$81.000.00</span>
        </div>
    </div>

    <!-- DETALLES -->
    <div class="section">
        <div class="section-title">Detalles</div>

        <div class="small-card">
            <span>Estado</span>
            <span>en mora</span>
        </div>
    </div>

    <!-- INFO -->
    <div class="info-box">
        Puedes realizar pagos anticipados para reducir intereses y mejorar tu historial crediticio.
    </div>

</div>

<!-- MODAL -->
<div class="modal" id="modal">
    <div class="modal-content" id="contenidoModal">
        <div class="spinner"></div>
        <h3>Procesando pago...</h3>
        <p>Conectando con el servidor...</p>
    </div>
</div>

<script>
function simularPago() {
    const modal = document.getElementById("modal");
    const contenido = document.getElementById("contenidoModal");

    modal.style.display = "flex";

    contenido.innerHTML = `
        <div class="spinner"></div>
        <h3>Procesando pago...</h3>
        <p>Conectando con el servidor...</p>
    `;

    setTimeout(() => {
        contenido.innerHTML = `
            <h3>ERROR DE CONECCION APP EN MANTENIMINETO</h3>
            <p style="color:#f87171;">No se pudo completar la transacción.</p>
            <p>Comuniquese con el area encargada para efectuar su pago.</p>
            <div class="close-btn" onclick="cerrarModal()">Cerrar</div>
        `;
    }, 2500);
}

function cerrarModal() {
    document.getElementById("modal").style.display = "none";
}
</script>

</body>
</html>
