<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SAMEST Estructuras | Cabañas Alpinas, Módulos y Herrería</title>
  <style>
    :root {
      --primary: #0D3A68;
      --primary-dark: #082544;
      --accent-green: #25D366;
      --accent-blue: #1D70B8;
      --bg-light: #F8FAFC;
      --card-bg: #FFFFFF;
      --text-main: #1E293B;
      --text-muted: #64748B;
      --border: #E2E8F0;
    }
    * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', system-ui, sans-serif; }
    body { background-color: var(--bg-light); color: var(--text-main); padding-bottom: 60px; }
    
    /* CABECERA Y HERO */
    header { background: linear-gradient(135deg, var(--primary-dark), var(--primary)); color: white; padding: 40px 20px; text-align: center; border-bottom-left-radius: 30px; border-bottom-right-radius: 30px; box-shadow: 0 10px 20px rgba(13, 58, 104, 0.15); }
    header h1 { font-size: 2rem; font-weight: 800; margin-bottom: 8px; letter-spacing: 1px; }
    header p { font-size: 1rem; color: #CBD5E1; max-width: 600px; margin: 0 auto; }
    .badge-hero { display: inline-block; background: rgba(37, 211, 102, 0.2); border: 1px solid var(--accent-green); color: #4ADE80; padding: 6px 14px; border-radius: 20px; font-size: 0.85rem; font-weight: bold; margin-bottom: 12px; }

    .container { max-width: 900px; margin: 0 auto; padding: 0 15px; }

    /* FILTROS DE CATEGORÍA */
    .filtros-container { display: flex; justify-content: center; gap: 10px; margin: 25px 0; flex-wrap: wrap; }
    .btn-filtro { background: var(--card-bg); border: 2px solid var(--border); color: var(--text-main); padding: 10px 18px; border-radius: 25px; font-weight: 600; cursor: pointer; transition: 0.3s; font-size: 0.9rem; }
    .btn-filtro.activo, .btn-filtro:hover { background: var(--primary); color: white; border-color: var(--primary); }

    /* GRILLA DE MODELOS/CATÁLOGO */
    .catalogo-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 25px; margin-bottom: 40px; }
    .card-modelo { background: var(--card-bg); border-radius: 18px; overflow: hidden; box-shadow: 0 6px 15px rgba(0,0,0,0.06); border: 1px solid var(--border); display: flex; flex-direction: column; }
    
    /* PESTAÑAS DE IMÁGENES EN TARJETA */
    .card-tabs { display: flex; background: #F1F5F9; border-bottom: 1px solid var(--border); }
    .tab-btn { flex: 1; padding: 8px 4px; border: none; background: transparent; font-size: 0.75rem; font-weight: bold; color: var(--text-muted); cursor: pointer; transition: 0.2s; }
    .tab-btn.activo { background: var(--card-bg); color: var(--primary); border-top: 2px solid var(--primary); }
    
    .img-container { height: 220px; overflow: hidden; position: relative; background: #E2E8F0; }
    .img-container img { width: 100%; height: 100%; object-fit: cover; display: none; }
    .img-container img.activa { display: block; }
    
    .card-body { padding: 20px; flex: 1; display: flex; flex-direction: column; justify-content: space-between; }
    .card-title { font-size: 1.2rem; color: var(--primary-dark); margin-bottom: 6px; }
    .card-desc { font-size: 0.85rem; color: var(--text-muted); line-height: 1.4; margin-bottom: 15px; }
    .card-specs { font-size: 0.8rem; background: var(--bg-light); padding: 10px; border-radius: 8px; margin-bottom: 15px; }
    .card-specs ul { list-style: none; }
    .card-specs li { margin-bottom: 4px; display: flex; align-items: center; gap: 6px; }

    /* BOTONES */
    .btn { width: 100%; padding: 12px; border: none; border-radius: 10px; font-size: 0.95rem; font-weight: bold; color: white; cursor: pointer; display: flex; justify-content: center; align-items: center; gap: 8px; text-decoration: none; transition: 0.2s; }
    .btn-green { background: var(--accent-green); }
    .btn-green:hover { background: #1EBE5D; }
    .btn-blue { background: var(--primary); }
    .btn-blue:hover { background: var(--primary-dark); }
    .btn-outline { background: transparent; border: 2px solid var(--primary); color: var(--primary); }
    .btn-outline:hover { background: var(--primary); color: white; }

    /* ESQUEMA DE PAGOS Y GARANTÍA */
    .garantia-box { background: linear-gradient(135deg, #1E293B, #0F172A); color: white; border-radius: 18px; padding: 30px 20px; margin: 40px 0; text-align: center; }
    .garantia-box h2 { color: #F8FAFC; margin-bottom: 15px; font-size: 1.4rem; }
    .pagos-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; margin-top: 20px; }
    .pago-step { background: rgba(255,255,255,0.05); border: 1px solid rgba(255,255,255,0.1); padding: 15px 8px; border-radius: 12px; }
    .pago-pct { font-size: 1.4rem; font-weight: 800; color: #4ADE80; }
    .pago-lbl { font-size: 0.75rem; color: #94A3B8; margin-top: 4px; }

    /* FORMULARIO VENTAS */
    .form-section { background: white; border-radius: 18px; padding: 30px 20px; box-shadow: 0 10px 25px rgba(0,0,0,0.08); margin-bottom: 40px; border: 1px solid var(--border); }
    .form-section h2 { color: var(--primary); font-size: 1.4rem; margin-bottom: 10px; }
    .form-group { margin-bottom: 15px; }
    label { display: block; font-size: 0.85rem; font-weight: 600; margin-bottom: 6px; }
    input, textarea, select { width: 100%; padding: 12px; border: 1.5px solid var(--border); border-radius: 10px; font-size: 0.95rem; background: #F8FAFC; }
    input:focus, textarea:focus, select:focus { border-color: var(--primary); background: white; outline: none; }

    /* SECCIONES COLAPSABLES (RRHH Y PROVEEDORES) */
    .sec-colapsable { background: white; border-radius: 12px; margin-bottom: 15px; border: 1px solid var(--border); overflow: hidden; }
    .colapsable-header { padding: 15px 20px; background: #F1F5F9; font-weight: bold; cursor: pointer; display: flex; justify-content: space-between; align-align: center; font-size: 0.95rem; color: var(--primary-dark); }
    .colapsable-body { padding: 20px; display: none; }

    /* FOOTER */
    footer { text-align: center; font-size: 0.85rem; color: var(--text-muted); padding: 30px 15px 10px; border-top: 1px solid var(--border); margin-top: 40px; }
    footer p { margin-bottom: 8px; }
  </style>
</head>
<body>

<header>
  <span class="badge-hero">⚡ Fabricación e Instalación Directa</span>
  <h1>SAMEST ESTRUCTURAS</h1>
  <p>Cabañas Alpinas A-Frame, Módulos Habitacionales, Mezzanines y Herrería Estructural de Alta Gama.</p>
</header>

<div class="container">

  <!-- FILTROS DE CATEGORÍA -->
  <div class="filtros-container">
    <button class="btn-filtro activo" onclick="filtrarCat('todos', this)">Todos los Modelos</button>
    <button class="btn-filtro" onclick="filtrarCat('cabanas', this)">🏡 Cabañas A-Frame</button>
    <button class="btn-filtro" onclick="filtrarCat('modulos', this)">📦 Módulos / Mezzanines</button>
    <button class="btn-filtro" onclick="filtrarCat('herreria', this)">🏗️ Herrería Estructural</button>
  </div>

  <!-- CATÁLOGO INTERACTIVO -->
  <div class="catalogo-grid">
    
    <!-- MODELO 1: CABAÑA A-FRAME -->
    <div class="card-modelo cabanas">
      <div class="card-tabs">
        <button class="tab-btn activo" onclick="cambiarTab(this, 'm1-f')">Fachada</button>
        <button class="tab-btn" onclick="cambiarTab(this, 'm1-pb')">Planta Baja</button>
        <button class="tab-btn" onclick="cambiarTab(this, 'm1-pa')">Planta Alta</button>
        <button class="tab-btn" onclick="cambiarTab(this, 'm1-est')">Esqueleto</button>
      </div>
      <div class="img-container">
        <img id="m1-f" class="activa" src="https://images.unsplash.com/photo-1510798831971-661eb04b3739?auto=format&fit=crop&w=600&q=80" alt="Cabaña A-Frame Fachada">
        <img id="m1-pb" src="https://images.unsplash.com/photo-1600585154340-be6161a56a0c?auto=format&fit=crop&w=600&q=80" alt="Planta Baja">
        <img id="m1-pa" src="https://images.unsplash.com/photo-1600566753376-12c8ab7fb75b?auto=format&fit=crop&w=600&q=80" alt="Planta Alta Tapanco">
        <img id="m1-est" src="https://images.unsplash.com/photo-1503387762-592deb58ef4e?auto=format&fit=crop&w=600&q=80" alt="Esqueleto Estructural Acero">
      </div>
      <div class="card-body">
        <div>
          <h3 class="card-title">Cabaña Alpina A-Frame Master</h3>
          <p class="card-desc">Estructura modular de acero IPR/PTR con ventanales panorámicos y tapanco de madera tratada.</p>
          <div class="card-specs">
            <ul>
              <li>📐 Medidas: 6m x 8m (48 m² + Tapanco)</li>
              <li>🛠️ Estructura: Acero estructural anticorrosivo</li>
              <li>⏱️ Tiempo de montaje: 15-20 días</li>
            </ul>
          </div>
        </div>
        <button class="btn btn-green" onclick="cotizarModelo('Cabaña Alpina A-Frame Master')">📲 Cotizar este Modelo</button>
      </div>
    </div>

    <!-- MODELO 2: MÓDULO HABITACIONAL / MEZZANINE -->
    <div class="card-modelo modulos">
      <div class="card-tabs">
        <button class="tab-btn activo" onclick="cambiarTab(this, 'm2-f')">Diseño</button>
        <button class="tab-btn" onclick="cambiarTab(this, 'm2-pb')">Planta</button>
        <button class="tab-btn" onclick="cambiarTab(this, 'm2-est')">Estructura</button>
      </div>
      <div class="img-container">
        <img id="m2-f" class="activa" src="https://images.unsplash.com/photo-1513694203232-719a280e022f?auto=format&fit=crop&w=600&q=80" alt="Módulo Loft">
        <img id="m2-pb" src="https://images.unsplash.com/photo-1600607687939-ce8a6c25118c?auto=format&fit=crop&w=600&q=80" alt="Planta Módulo">
        <img id="m2-est" src="https://images.unsplash.com/photo-1581092580497-e0d23cbdf1dc?auto=format&fit=crop&w=600&q=80" alt="Estructura Mezzanine">
      </div>
      <div class="card-body">
        <div>
          <h3 class="card-title">Módulo Loft / Mezzanine Industrial</h3>
          <p class="card-desc">Solución espacial de alta resistencia ideal para oficinas, departamentos modulares o ampliaciones.</p>
          <div class="card-specs">
            <ul>
              <li>📐 Medidas: Adaptables según espacio</li>
              <li>🛠️ Vigas IPR y lozacero reforzada</li>
              <li>⏱️ Instalación rápida sin obra negra pesada</li>
            </ul>
          </div>
        </div>
        <button class="btn btn-green" onclick="cotizarModelo('Módulo Loft / Mezzanine Industrial')">📲 Cotizar este Modelo</button>
      </div>
    </div>

    <!-- MODELO 3: HERRERÍA Y ZAGUANES DE ALTA GAMA -->
    <div class="card-modelo herreria">
      <div class="card-tabs">
        <button class="tab-btn activo" onclick="cambiarTab(this, 'm3-f')">Diseño</button>
        <button class="tab-btn" onclick="cambiarTab(this, 'm3-est')">Detalle</button>
      </div>
      <div class="img-container">
        <img id="m3-f" class="activa" src="https://images.unsplash.com/photo-1621252179027-94459d278660?auto=format&fit=crop&w=600&q=80" alt="Zaguán Moderno">
        <img id="m3-est" src="https://images.unsplash.com/photo-1504307651254-35680f356f12?auto=format&fit=crop&w=600&q=80" alt="Acabados en Herrería">
      </div>
      <div class="card-body">
        <div>
          <h3 class="card-title">Zaguanes, Portones y Pergolados</h3>
          <p class="card-desc">Diseños contemporáneos, portones automatizados, pergolados y protecciones de alta seguridad.</p>
          <div class="card-specs">
            <ul>
              <li>📐 Fabricación 100% a la medida</li>
              <li>🛠️ Pintura electrostática / poliuretano</li>
              <li>🔒 Garantía por escrito en soldadura</li>
            </ul>
          </div>
        </div>
        <button class="btn btn-green" onclick="cotizarModelo('Zaguanes y Herrería Residencial')">📲 Cotizar Herrería</button>
      </div>
    </div>

  </div>

  <!-- ESQUEMA DE PAGOS Y GARANTÍA SAMEST -->
  <div class="garantia-box">
    <h2>🛡️ Garantía y Esquema de Trabajo SAMEST</h2>
    <p style="font-size: 0.9rem; color: #CBD5E1; max-width: 650px; margin: 0 auto;">Trabajamos bajo contrato con fechas de entrega garantizadas y transparencia total en cada etapa constructiva.</p>
    <div class="pagos-grid">
      <div class="pago-step">
        <div class="pago-pct">50%</div>
        <div class="pago-lbl">Anticipo y firma de contrato</div>
      </div>
      <div class="pago-step">
        <div class="pago-pct">25%</div>
        <div class="pago-lbl">Avance de armado en taller</div>
      </div>
      <div class="pago-step">
        <div class="pago-pct">25%</div>
        <div class="pago-lbl">Entrega e instalación final</div>
      </div>
    </div>
  </div>

  <!-- FORMULARIO DE COTIZACIÓN RÁPIDA -->
  <div id="formularioCotizacion" class="form-section">
    <h2>📋 Solicita tu Cotización Personalizada</h2>
    <p style="font-size: 0.85rem; color: var(--text-muted); margin-bottom: 20px;">Completa los datos y te responderemos con presupuesto y asesoría técnica por WhatsApp.</p>
    <form onsubmit="event.preventDefault(); enviarFormularioGeneral();">
      <div class="form-group">
        <label>Nombre Completo</label>
        <input type="text" id="cNombre" required placeholder="Ej. Carlos Mendoza">
      </div>
      <div class="form-group">
        <label>Código Postal (Indispensable para cálculo de flete)</label>
        <input type="number" id="cCP" required placeholder="Ej. 56530">
      </div>
      <div class="form-group">
        <label>Proyecto de Interés</label>
        <select id="cProyecto">
          <option value="Cabaña Alpina A-Frame">Cabaña Alpina A-Frame</option>
          <option value="Módulo Habitacional / Loft">Módulo Habitacional / Loft</option>
          <option value="Mezzanine Estructural">Mezzanine Estructural</option>
          <option value="Zaguán / Portón Automatizado">Zaguán / Portón Automatizado</option>
          <option value="Techado / Pérgola">Techado / Pérgola</option>
          <option value="Otro Trabajo Especial">Otro Trabajo Especial</option>
        </select>
      </div>
      <div class="form-group">
        <label>Medidas aprox. y detalles del terreno u obra</label>
        <textarea id="cDetalles" rows="3" placeholder="Ej. Terreno plano de 10x15m en zona fría, busco cabaña de 2 recámaras..."></textarea>
      </div>
      <button type="submit" class="btn btn-green" style="font-size: 1.05rem;">📲 Enviar Cotización por WhatsApp</button>
    </form>
  </div>

  <!-- SECCIONES SECUNDARIAS COLAPSABLES -->
  <div class="sec-colapsable">
    <div class="colapsable-header" onclick="toggleColapsable('bodyRRHH')">
      <span>👷 Bolsa de Trabajo (Contrataciones)</span>
      <span>▼</span>
    </div>
    <div id="bodyRRHH" class="colapsable-body">
      <p style="font-size: 0.85rem; margin-bottom: 12px; color: var(--text-muted);">¿Eres soldador, pailero o ayudante? Déjanos tus datos para ingresar a nuestra lista de espera prioritarias.</p>
      <div class="form-group"><label>Nombre</label><input type="text" id="rhNombre"></div>
      <div class="form-group"><label>Especialidad</label><input type="text" id="rhPuesto" placeholder="Ej. Soldador Argonero"></div>
      <button class="btn btn-blue" onclick="enviarRRHH()">Enviar Solicitud 🚀</button>
    </div>
  </div>

  <div class="sec-colapsable">
    <div class="colapsable-header" onclick="toggleColapsable('bodyProv')">
      <span>🤝 Portal de Proveedores</span>
      <span>▼</span>
    </div>
    <div id="bodyProv" class="colapsable-body">
      <p style="font-size: 0.85rem; margin-bottom: 12px; color: var(--text-muted);">Ofrece tus insumos, aceros o servicios a nuestro departamento de compras.</p>
      <div class="form-group"><label>Empresa</label><input type="text" id="pEmpresa"></div>
      <div class="form-group"><label>Material/Servicio</label><input type="text" id="pMaterial"></div>
      <button class="btn btn-blue" onclick="enviarProv()">Enviar Propuesta Comercial 📊</button>
    </div>
  </div>

</div>

<footer>
  <p><strong>SAMEST ESTRUCTURAS</strong> &mdash; Ixtapaluca, Estado de México</p>
  <p>📍 Cobertura de fabricación e instalación en todo el centro del país.</p>
  <p style="margin-top: 10px;">
    <a href="https://instagram.com/samest" target="_blank" style="color: var(--primary); font-weight: bold; text-decoration: none;">Instagram</a> | 
    <a href="https://facebook.com" target="_blank" style="color: var(--primary); font-weight: bold; text-decoration: none;">Facebook</a>
  </p>
</footer>

<script>
  const NUMERO_WA = "525645855721";
  const LINK_REDES = "https://instagram.com/samest";

  function cambiarTab(btn, imgId) {
    const card = btn.closest('.card-modelo');
    card.querySelectorAll('.tab-btn').forEach(t => t.classList.remove('activo'));
    card.querySelectorAll('.img-container img').forEach(i => i.classList.remove('activa'));
    btn.classList.add('activo');
    document.getElementById(imgId).classList.add('activa');
  }

  function filtrarCat(cat, btn) {
    document.querySelectorAll('.btn-filtro').forEach(b => b.classList.remove('activo'));
    btn.classList.add('activo');
    document.querySelectorAll('.card-modelo').forEach(card => {
      if(cat === 'todos' || card.classList.contains(cat)) {
        card.style.display = 'flex';
      } else {
        card.style.display = 'none';
      }
    });
  }

  function toggleColapsable(id) {
    const el = document.getElementById(id);
    el.style.display = (el.style.display === 'block') ? 'none' : 'block';
  }

  function cotizarModelo(nombreModelo) {
    const msg = `¡Hola SAMEST! Me interesa cotizar el modelo: *${nombreModelo}*.\n\nPor favor requiero asesoría sobre dimensiones y presupuesto de envío.`;
    window.open(`https://wa.me/${NUMERO_WA}?text=${encodeURIComponent(msg)}`, '_blank');
  }

  function enviarFormularioGeneral() {
    const nom = document.getElementById('cNombre').value || "Cliente";
    const cp = document.getElementById('cCP').value || "No especificado";
    const proy = document.getElementById('cProyecto').value;
    const det = document.getElementById('cDetalles').value || "Sin detalles adicionales";

    const msg = `¡Hola SAMEST! Solicito cotización desde la web.\n\n👤 *Nombre:* ${nom}\n📍 *C.P.:* ${cp}\n🏗️ *Proyecto:* ${proy}\n📏 *Detalles:* ${det}`;
    window.open(`https://wa.me/${NUMERO_WA}?text=${encodeURIComponent(msg)}`, '_blank');
  }

  function enviarRRHH() {
    const nom = document.getElementById('rhNombre').value || "Candidato";
    const puesto = document.getElementById('rhPuesto').value || "Sin especificar";
    const msg = `👷‍♂️ *BOLSA DE TRABAJO*\nHola, soy ${nom}. Me postulo como *${puesto}*.`;
    window.open(`https://wa.me/${NUMERO_WA}?text=${encodeURIComponent(msg)}`, '_blank');
  }

  function enviarProv() {
    const emp = document.getElementById('pEmpresa').value || "Empresa";
    const mat = document.getElementById('pMaterial').value || "Insumos";
    const msg = `🤝 *PORTAL PROVEEDORES*\nSomos *${emp}*. Ofrecemos: ${mat}.`;
    window.open(`https://wa.me/${NUMERO_WA}?text=${encodeURIComponent(msg)}`, '_blank');
  }
</script>

<body>
</html>
