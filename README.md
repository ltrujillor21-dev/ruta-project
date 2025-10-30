[dashboard.html](https://github.com/user-attachments/files/23243887/dashboard.html)
<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>LogiRoutes — Dashboard</title>
  <link rel="stylesheet" href="style.css">
  <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css"/>
</head>
<body class="dashboard-body">

  <aside class="sidebar">
    <div class="side-brand">
      <div class="logo-sm">
        <svg width="28" height="28" viewBox="0 0 24 24" fill="none">
          <rect x="2" y="6" width="20" height="12" rx="2" fill="#0b63d4"/>
        </svg>
      </div>
      <div>
        <strong>LogiRoutes</strong>
        <small class="muted">Gestión logística</small>
      </div>
    </div>

    <nav class="nav">
      <button class="nav-item active" data-target="dashboard">Dashboard</button>
      <button class="nav-item" data-target="rutas">Rutas</button>
      <button class="nav-item" data-target="estadisticas">Estadísticas</button>
      <button class="nav-item" data-target="config">Configuración</button>
    </nav>

    <div class="side-footer muted small">Usuario: <strong>admin</strong></div>
  </aside>

  <div class="main-area">
    <header class="topbar">
      <div class="search">
        <input id="globalSearch" placeholder="Buscar conductor, vehículo o ruta...">
      </div>
      <div class="top-actions">
        <button id="newRouteBtn" class="btn small">+ Nueva Ruta</button>
        <button id="logoutBtn" class="btn ghost small">Cerrar sesión</button>
      </div>
    </header>

    <section class="container" id="dashboardSection">
      <!-- Estadísticas -->
      <div class="stats-grid">
        <div class="stat-card">
          <div class="stat-left">
            <h3 id="totalRoutes">0</h3>
            <p class="muted">Rutas activas</p>
          </div>
          <div class="stat-right mini">🚚</div>
        </div>

        <div class="stat-card">
          <div class="stat-left">
            <h3 id="onRoute">0</h3>
            <p class="muted">En ruta</p>
          </div>
          <div class="stat-right mini">🟦</div>
        </div>

        <div class="stat-card">
          <div class="stat-left">
            <h3 id="delivered">0</h3>
            <p class="muted">Entregadas</p>
          </div>
          <div class="stat-right mini">✅</div>
        </div>

        <div class="stat-card">
          <div class="stat-left">
            <h3 id="pending">0</h3>
            <p class="muted">Pendientes</p>
          </div>
          <div class="stat-right mini">⏳</div>
        </div>
      </div>

      <!-- Charts + mapa interactivo -->
      <div class="panel-grid">
        <div class="panel card">
          <h4>Rendimiento — Últimas 7 rutas</h4>
          <canvas id="sparkChart" height="120"></canvas>
        </div>

        <div class="panel card">
          <h4>Mapa Interactivo</h4>
          <div id="map" style="height:300px; border-radius:8px;"></div>
        </div>
      </div>

      <!-- Lista de rutas -->
      <div class="card">
        <div class="card-header">
          <h4>Lista de Rutas</h4>
          <div>
            <select id="filterState">
              <option value="all">Todos</option>
              <option value="pendiente">Pendiente</option>
              <option value="enruta">En ruta</option>
              <option value="entregado">Entregado</option>
            </select>
          </div>
        </div>

        <div id="routesList" class="routes-list"></div>
      </div>
    </section>
  </div>

  <!-- Modal -->
  <div id="modal" class="modal hidden" aria-hidden="true">
    <div class="modal-panel card">
      <button id="closeModal" class="modal-close">×</button>
      <div id="modalContent"></div>
    </div>
  </div>

  <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
  <script src="script.js"></script>
</body>
</html>
