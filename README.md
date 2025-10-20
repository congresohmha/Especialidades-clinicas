<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> I CONGRESO INTERNACIONAL DE ESPECIALIDADES CLINICAS-QUIRURGICAS | HOSPITAL MIGUEL H. ALCIVAR 2025</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700&family=Open+Sans:wght@400;600&family=Roboto+Mono&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.10.1/jszip.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/FileSaver.js/2.0.5/FileSaver.min.js"></script>
    <style>
        :root {
            --primary-blue: #1a4a7a;
            --secondary-blue: #2c6aa4;
            --white: #ffffff;
            --light-gray: #f8f9fa;
            --medium-gray: #e9ecef;
            --dark-gray: #495057;
            --success-green: #28a745;
            --alert-red: #dc3545;
            --countdown-orange: #fd7e14;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Open Sans', sans-serif;
            color: var(--dark-gray);
            background-color: var(--light-gray);
            line-height: 1.6;
        }

        h1, h2, h3, h4, h5, h6 {
            font-family: 'Montserrat', sans-serif;
            font-weight: 600;
            margin-bottom: 1rem;
        }****

        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header Section */
        .header {
            background-color: var(--primary-blue);
            color: var(--white);
            padding: 1rem 0;
            border-bottom: 3px solid var(--secondary-blue);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
        }

        .organizer-info {
            flex: 1;
            min-width: 300px;
        }

        .organizer-info h2 {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
        }

        .contact-info {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            font-size: 0.9rem;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .brochure-link {
            background-color: var(--secondary-blue);
            color: var(--white);
            padding: 1rem 1.5rem;
            border-radius: 8px;
            text-decoration: none;
            font-weight: 700;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 0.75rem;
            font-size: 1.1rem;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        .brochure-link:hover {
            background-color: #1a4a7a;
            transform: translateY(-3px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(135deg, var(--primary-blue) 0%, var(--secondary-blue) 100%);
            color: var(--white);
            padding: 4rem 0;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero-content {
            position: relative;
            z-index: 2;
        }

        .logo-container {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 1.5rem;
        }

        .logo {
            height: 80px;
            margin-right: 20px;
        }

        .hero h1 {
            font-size: 2.5rem;
            margin-bottom: 1.5rem;
            font-weight: 700;
        }

        .countdown {
            font-family: 'Roboto Mono', monospace;
            font-size: 2rem;
            margin: 2rem 0;
            background-color: rgba(0, 0, 0, 0.2);
            padding: 1rem;
            border-radius: 8px;
            display: inline-block;
        }

        .badges {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin: 1.5rem 0;
        }

        .badge {
            background-color: var(--countdown-orange);
            padding: 0.5rem 1rem;
            border-radius: 20px;
            font-weight: 600;
            font-size: 0.9rem;
        }

        .cta-button {
            display: inline-block;
            background-color: var(--success-green);
            color: var(--white);
            padding: 1rem 2rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            font-size: 1.2rem;
            margin-top: 1rem;
            transition: all 0.3s ease;
        }

        .cta-button:hover {
            background-color: #218838;
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }

        /* Cards Section */
        .cards-section {
            padding: 4rem 0;
        }

        .section-title {
            text-align: center;
            margin-bottom: 3rem;
            color: var(--primary-blue);
        }

        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .card {
            background-color: var(--white);
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
        }

        .card:hover {
            transform: translateY(-5px);
        }

        .card-header {
            background-color: var(--primary-blue);
            color: var(--white);
            padding: 1.5rem;
            text-align: center;
        }

        .card-body {
            padding: 1.5rem;
        }

        .card-icon {
            font-size: 2rem;
            margin-bottom: 1rem;
            color: var(--primary-blue);
        }

        .capacity-counter {
            font-size: 1.2rem;
            font-weight: 600;
            color: var(--primary-blue);
            margin: 1rem 0;
        }

        /* Registration Section */
        .registration-section {
            padding: 4rem 0;
            background-color: var(--medium-gray);
        }

        .registration-form {
            max-width: 600px;
            margin: 0 auto;
            background-color: var(--white);
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
        }

        input, select {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid var(--medium-gray);
            border-radius: 5px;
            font-family: 'Open Sans', sans-serif;
        }

        .submit-btn {
            width: 100%;
            padding: 1rem;
            background-color: var(--primary-blue);
            color: var(--white);
            border: none;
            border-radius: 5px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .submit-btn:hover {
            background-color: var(--secondary-blue);
        }

        .submit-btn:disabled {
            background-color: var(--medium-gray);
            cursor: not-allowed;
        }

        /* Agenda & Certificates Section */
        .agenda-certificates {
            padding: 4rem 0;
        }

        .agenda-container, .certificates-container {
            background-color: var(--white);
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            margin-bottom: 2rem;
        }

        .status-badge {
            display: inline-block;
            padding: 0.5rem 1rem;
            border-radius: 20px;
            font-weight: 600;
            margin-top: 1rem;
        }

        .status-pending {
            background-color: var(--countdown-orange);
            color: var(--white);
        }

        .status-available {
            background-color: var(--success-green);
            color: var(--white);
        }

        .status-unavailable {
            background-color: var(--medium-gray);
            color: var(--dark-gray);
        }

        /* Admin Panel */
        .admin-panel {
            padding: 2rem 0;
            display: none;
        }

        .admin-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
            padding-bottom: 1rem;
            border-bottom: 1px solid var(--medium-gray);
        }

        .admin-tabs {
            display: flex;
            border-bottom: 1px solid var(--medium-gray);
            margin-bottom: 2rem;
            flex-wrap: wrap;
        }

        .admin-tab {
            padding: 1rem 2rem;
            background: none;
            border: none;
            cursor: pointer;
            font-family: 'Montserrat', sans-serif;
            font-weight: 600;
            border-bottom: 3px solid transparent;
        }

        .admin-tab.active {
            border-bottom: 3px solid var(--primary-blue);
            color: var(--primary-blue);
        }

        .admin-content {
            display: none;
        }

        .admin-content.active {
            display: block;
        }

        .dashboard-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
            margin-bottom: 2rem;
        }

        .stat-card {
            background-color: var(--white);
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
            text-align: center;
        }

        .stat-number {
            font-size: 2rem;
            font-weight: 700;
            color: var(--primary-blue);
        }

        .participants-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1rem;
        }

        .participants-table th, .participants-table td {
            padding: 0.75rem;
            text-align: left;
            border-bottom: 1px solid var(--medium-gray);
        }

        .participants-table th {
            background-color: var(--primary-blue);
            color: var(--white);
        }

        .action-buttons {
            display: flex;
            gap: 0.5rem;
        }

        .btn {
            padding: 0.5rem 1rem;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-family: 'Open Sans', sans-serif;
            font-weight: 600;
            transition: background-color 0.3s ease;
        }

        .btn-primary {
            background-color: var(--primary-blue);
            color: var(--white);
        }

        .btn-success {
            background-color: var(--success-green);
            color: var(--white);
        }

        .btn-danger {
            background-color: var(--alert-red);
            color: var(--white);
        }

        .btn-secondary {
            background-color: var(--medium-gray);
            color: var(--dark-gray);
        }

        .btn-warning {
            background-color: var(--countdown-orange);
            color: var(--white);
        }

        .file-upload {
            border: 2px dashed var(--medium-gray);
            padding: 2rem;
            text-align: center;
            border-radius: 8px;
            margin-bottom: 1rem;
        }

        .file-upload.active {
            border-color: var(--primary-blue);
            background-color: rgba(26, 74, 122, 0.05);
        }

        .attendance-forms {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1rem;
            margin-bottom: 2rem;
        }

        .attendance-form {
            background-color: var(--white);
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
        }

        .certificate-template {
            margin-bottom: 2rem;
        }

        /* Search and Filters */
        .search-filters {
            display: flex;
            gap: 1rem;
            margin-bottom: 1.5rem;
            flex-wrap: wrap;
        }

        .search-box {
            flex: 1;
            min-width: 250px;
        }

        .filter-select {
            min-width: 150px;
        }

        /* Login Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            background-color: var(--white);
            padding: 2rem;
            border-radius: 10px;
            width: 90%;
            max-width: 400px;
        }

        .modal-header {
            margin-bottom: 1.5rem;
            text-align: center;
        }

        .close-modal {
            float: right;
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* Map Styles */
        .map-container {
            height: 200px;
            margin-top: 1rem;
            border-radius: 8px;
            overflow: hidden;
        }

        /* Edit Modal */
        .edit-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .edit-modal-content {
            background-color: var(--white);
            padding: 2rem;
            border-radius: 10px;
            width: 90%;
            max-width: 500px;
            max-height: 90vh;
            overflow-y: auto;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 1rem;
                text-align: center;
            }

            .hero h1 {
                font-size: 1.8rem;
            }

            .countdown {
                font-size: 1.5rem;
            }

            .badges {
                flex-direction: column;
                align-items: center;
            }

            .admin-tabs {
                flex-direction: column;
            }

            .admin-tab {
                border-bottom: 1px solid var(--medium-gray);
                border-left: 3px solid transparent;
            }

            .admin-tab.active {
                border-left: 3px solid var(--primary-blue);
                border-bottom: 1px solid var(--medium-gray);
            }

            .search-filters {
                flex-direction: column;
            }
        }

        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid rgba(255,255,255,.3);
            border-radius: 50%;
            border-top-color: #fff;
            animation: spin 1s ease-in-out infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* Nuevos estilos para mejoras solicitadas */
        .date-display {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 0.5rem;
        }

        .date-main {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--primary-blue);
        }

        .date-year {
            font-size: 1.2rem;
            font-weight: 600;
            color: var(--secondary-blue);
        }

        .capacity-info {
            font-size: 1.1rem;
            font-weight: 600;
            color: var(--primary-blue);
            margin: 1rem 0;
            text-align: center;
        }
    </style>
</head>
<body>
    <!-- Header Section -->
    <header class="header">
        <div class="container">
            <div class="header-content">
                <div class="organizer-info">
                    <h2>UNIDAD DE DOCENCIA E INVESTIGACIÓN</h2>
                    <p>Hospital Miguel H. Alcivar</p>
                    <div class="contact-info">
                        <div class="contact-item">
                            <i class="fas fa-envelope"></i>
                            <span>docenciahmha2023@gmail.com</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-phone"></i>
                            <span>0991708712</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-user-md"></i>
                            <span>Dr. Julio Feijoo - Analista de Docencia</span>
                        </div>
                    </div>
                </div>
                <a href="https://www.canva.com/design/DAGxPEDGSwU/hq3RFABqYJqYkuVMhQWBag/watch?utm_content=DAGxPEDGSwU&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=h2671635ad9" target="_blank" class="brochure-link">
                    <i class="fas fa-book-open"></i>
                    Ver Información del Congreso
                </a>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="container">
            <div class="hero-content">
                <div class="logo-container">
                    <img src="https://via.placeholder.com/80x80/1a4a7a/ffffff?text=MH" alt="Hospital Miguel H. Alcivar" class="logo">
                    <h1>I ER CONGRESO INTERNACIONAL DE ESPECIALIDADES CLINICAS-QUIRURGICAS</h1>
                </div>
                <div class="countdown" id="countdown">
                    <span id="days">00</span>d <span id="hours">00</span>h <span id="minutes">00</span>m <span id="seconds">00</span>s
                </div>
                <div class="badges">
                    <div class="badge">GRATUITO</div>
                    <div class="badge">CUPOS LIMITADOS: 220</div>
                </div>
                <a href="#registration" class="cta-button">Registrarse Ahora</a>
            </div>
        </div>
    </section>

    <!-- Information Cards -->
    <section class="cards-section">
        <div class="container">
            <h2 class="section-title">Información Esencial</h2>
            <div class="cards-grid">
                <div class="card">
                    <div class="card-header">
                        <h3>Fechas</h3>
                    </div>
                    <div class="card-body">
                        <i class="fas fa-calendar-alt card-icon"></i>
                        <div class="date-display">
                            <div class="date-main">23-25 Octubre</div>
                            <div class="date-year">2025</div>
                        </div>
                    </div>
                </div>
                <div class="card">
                    <div class="card-header">
                        <h3>Lugar</h3>
                    </div>
                    <div class="card-body">
                        <i class="fas fa-map-marker-alt card-icon"></i>
                        <p>BAHIA DE CARAQUEZ, DESTINO UNICO EN MANABI</p>
                        <p>Auditorio ULEAM BAHIA DE CARAQUEZ EXTENSION SUCRE</p>
                        <div class="map-container">
                            <iframe 
                                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3989.267441346091!2d-80.427545!3d-0.5975!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x902b6b8a5f0c0001%3A0x8c5e5e5e5e5e5e5e!2sBah%C3%ADa%20de%20Car%C3%A1quez%2C%20Ecuador!5e0!3m2!1ses!2ses!4v1690000000000!5m2!1ses!2ses" 
                                width="100%" 
                                height="200" 
                                style="border:0;" 
                                allowfullscreen="" 
                                loading="lazy" 
                                referrerpolicy="no-referrer-when-downgrade">
                            </iframe>
                        </div>
                    </div>
                </div>
                <div class="card">
                    <div class="card-header">
                        <h3>Capacidad</h3>
                    </div>
                    <div class="card-body">
                        <i class="fas fa-users card-icon"></i>
                        <p class="capacity-info">CUPOS AGOTADOS</p>
                        <!-- Información de cupos disponibles solo visible para administradores -->
                        <div class="capacity-counter" id="admin-capacity-info" style="display: none;">
                            <span id="available-slots">50</span> cupos disponibles para DR./DRA.
                        </div>
                    </div>
                </div>
                <div class="card">
                    <div class="card-header">
                        <h3>Certificados</h3>
                    </div>
                    <div class="card-body">
                        <i class="fas fa-certificate card-icon"></i>
                        <p>Disponibles a partir del 27 de Octubre 2025, 8:00</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Registration Section -->
    <section class="registration-section" id="registration">
        <div class="container">
            <h2 class="section-title">Registro</h2>
            <div class="registration-form">
                <form id="registration-form">
                    <div class="form-group">
                        <label for="cargo">Cargo *</label>
                        <select id="cargo" name="cargo" required>
                            <option value="">Seleccione su cargo</option>
                            <option value="DR.">DR.</option>
                            <option value="DRA.">DRA.</option>
                            <option value="LCDO.">LCDO.</option>
                            <option value="LCDA.">LCDA.</option>
                            <option value="IRM.">IRM.</option>
                            <option value="IRE.">IRE.</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="nombre">Nombre *</label>
                        <input type="text" id="nombre" name="nombre" required>
                    </div>
                    <div class="form-group">
                        <label for="apellido">Apellido *</label>
                        <input type="text" id="apellido" name="apellido" required>
                    </div>
                    <div class="form-group">
                        <label for="email">Email *</label>
                        <input type="email" id="email" name="email" required>
                    </div>
                    <div class="form-group">
                        <label for="categoria">Categoría *</label>
                        <select id="categoria" name="categoria" required>
                            <option value="">Seleccione su categoría</option>
                            <option value="Médico General">Médico General</option>
                            <option value="Especialista">Especialista</option>
                            <option value="Otro">Otro</option>
                        </select>
                    </div>
                    <button type="submit" class="submit-btn" id="submit-btn">Registrarse</button>
                </form>
                <div id="registration-message" style="margin-top: 1rem;"></div>
            </div>
        </div>
    </section>

    <!-- Agenda & Certificates Section -->
    <section class="agenda-certificates">
        <div class="container">
            <h2 class="section-title">Agenda & Certificados</h2>
            <div class="agenda-container">
                <h3>Agenda del Congreso</h3>
                <p>La agenda completa del congreso está disponible en los siguientes enlaces:</p>
                <div style="display: flex; flex-direction: column; gap: 1rem; margin-top: 1rem;">
                    <a href="https://www.canva.com/design/DAGviQzNOHg/TEdQktBuK4jmsez6md4o1Q/watch?utm_content=DAGviQzNOHg&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=h7ace130b42" 
                       target="_blank" class="cta-button" style="padding: 0.75rem 1.5rem; font-size: 1rem;">
                        <i class="fas fa-external-link-alt"></i> Agenda Jueves 23
                    </a>
                    <a href="https://www.canva.com/design/DAGvnJ0sKWg/P9bBMb4_9RMxwjsn-U6L1A/watch?utm_content=DAGvnJ0sKWg&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=h3de5508bd7" 
                       target="_blank" class="cta-button" style="padding: 0.75rem 1.5rem; font-size: 1rem;">
                        <i class="fas fa-external-link-alt"></i> Agenda Viernes 24
                    </a>
                    <a href="https://www.canva.com/design/DAGvnl0xCEU/BGl0NXd5kBGS6nBUaSS96g/watch?utm_content=DAGvnl0xCEU&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=hdbc43ce954" 
                       target="_blank" class="cta-button" style="padding: 0.75rem 1.5rem; font-size: 1rem;">
                        <i class="fas fa-external-link-alt"></i> Agenda Sábado 25
                    </a>
                </div>
                <div class="status-badge status-available">Disponible</div>
            </div>
            <div class="certificates-container">
                <h3>Certificados de Participación</h3>
                <p>Los certificados estarán disponibles para descarga a partir del 27 de Octubre 2025, 8:00</p>
                <div class="status-badge status-unavailable">No Disponible</div>
            </div>
        </div>
    </section>

    <!-- Admin Login Button -->
    <div class="container" style="text-align: center; margin: 2rem 0;">
        <button id="admin-login-btn" class="btn btn-primary">Acceso Administrativo</button>
    </div>

    <!-- Admin Panel -->
    <section class="admin-panel" id="admin-panel">
        <div class="container">
            <div class="admin-header">
                <h2>Panel de Administración</h2>
                <button id="admin-logout" class="btn btn-secondary">Cerrar Sesión</button>
            </div>
            
            <div class="admin-tabs">
                <button class="admin-tab active" data-tab="participants">Gestión de Participantes</button>
                <button class="admin-tab" data-tab="attendance">Control de Asistencias</button>
                <button class="admin-tab" data-tab="certificates">Enlace de Certificados</button>
            </div>
            
            <!-- Participants Management -->
            <div class="admin-content active" id="participants-content">
                <div class="dashboard-stats">
                    <div class="stat-card">
                        <div class="stat-number" id="total-slots">220</div>
                        <div>Cupos Totales</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="assigned-slots">0</div>
                        <div>Total Inscritos</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="public-available-slots">50</div>
                        <div>Cupos Públicos Disponibles</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="preassigned-used-slots">0</div>
                        <div>Preasignados Usados</div>
                    </div>
                </div>
                
                <h3>Registrar Nuevo Participante</h3>
                <form id="admin-registration-form">
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;">
                        <div class="form-group">
                            <label for="admin-cargo">Cargo</label>
                            <select id="admin-cargo" name="cargo" required>
                                <option value="DR.">DR.</option>
                                <option value="DRA.">DRA.</option>
                                <option value="LCDO.">LCDO.</option>
                                <option value="LCDA.">LCDA.</option>
                                <option value="IRM.">IRM.</option>
                                <option value="IRE.">IRE.</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label for="admin-categoria">Categoría</label>
                            <select id="admin-categoria" name="categoria" required>
                                <option value="Médico General">Médico General</option>
                                <option value="Especialista">Especialista</option>
                                <option value="Otro">Otro</option>
                            </select>
                        </div>
                    </div>
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;">
                        <div class="form-group">
                            <label for="admin-nombre">Nombre</label>
                            <input type="text" id="admin-nombre" name="nombre" required>
                        </div>
                        <div class="form-group">
                            <label for="admin-apellido">Apellido</label>
                            <input type="text" id="admin-apellido" name="apellido" required>
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="admin-email">Email</label>
                        <input type="email" id="admin-email" name="email" required>
                    </div>
                    <div class="form-group">
                        <label for="admin-tipo-registro">Tipo de Registro</label>
                        <select id="admin-tipo-registro" name="tipo_registro" required>
                            <option value="publico">Público</option>
                            <option value="preasignado">Preasignado</option>
                        </select>
                    </div>
                    <button type="submit" class="btn btn-primary">Registrar Participante</button>
                </form>
                
                <h3 style="margin-top: 2rem;">Lista de Participantes</h3>
                <div class="search-filters">
                    <div class="search-box form-group">
                        <input type="text" id="search-participants" placeholder="Buscar por nombre, apellido, email o cargo...">
                    </div>
                    <div class="filter-select form-group">
                        <select id="filter-cargo">
                            <option value="">Todos los cargos</option>
                            <option value="DR.">DR.</option>
                            <option value="DRA.">DRA.</option>
                            <option value="LCDO.">LCDO.</option>
                            <option value="LCDA.">LCDA.</option>
                            <option value="IRM.">IRM.</option>
                            <option value="IRE.">IRE.</option>
                        </select>
                    </div>
                    <div class="filter-select form-group">
                        <select id="filter-categoria">
                            <option value="">Todas las categorías</option>
                            <option value="Médico General">Médico General</option>
                            <option value="Especialista">Especialista</option>
                            <option value="Otro">Otro</option>
                        </select>
                    </div>
                    <div class="filter-select form-group">
                        <select id="filter-tipo-registro">
                            <option value="">Todos los tipos</option>
                            <option value="publico">Público</option>
                            <option value="preasignado">Preasignado</option>
                        </select>
                    </div>
                </div>
                <table class="participants-table">
                    <thead>
                        <tr>
                            <th>Cedula</th>
                            <th>Nombre</th>
                            <th>Email</th>
                            <th>Cargo</th>
                            <th>Categoría</th>
                            <th>Tipo</th>
                            <th>Acciones</th>
                        </tr>
                    </thead>
                    <tbody id="participants-table-body">
                        <!-- Participants will be loaded here -->
                    </tbody>
                </table>
                <button id="export-csv" class="btn btn-success" style="margin-top: 1rem;">Exportar a CSV</button>
            </div>
            
            
                
                <h3>Estadísticas de Asistencia</h3>
                <div class="dashboard-stats">
                    <div class="stat-card">
                        <div class="stat-number" id="total-participants">0</div>
                        <div>Total Participantes</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="approved-participants">0</div>
                        <div>Aprobados (2/3)</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="pending-participants">0</div>
                        <div>Pendientes</div>
                    </div>
                </div>
                
                <h3>Detalle de Asistencias</h3>
                <div class="search-filters">
                    <div class="search-box form-group">
                        <input type="text" id="search-attendance" placeholder="Buscar participantes...">
                    </div>
                    <div class="filter-select form-group">
                        <select id="filter-attendance-status">
                            <option value="">Todos los estados</option>
                            <option value="Aprobado">Aprobado</option>
                            <option value="No Aprobado">No Aprobado</option>
                        </select>
                    </div>
                </div>
                <table class="participants-table">
                    <thead>
                        <tr>
                            <th>Nombre</th>
                            <th>Jue 23</th>
                            <th>Vie 24</th>
                            <th>Sab 25</th>
                            <th>Estado</th>
                            <th>Acciones</th>
                        </tr>
                    </thead>
                    <tbody id="attendance-table-body">
                        <!-- Attendance data will be loaded here -->
                    </tbody>
                </table>
                <button id="export-attendance" class="btn btn-success" style="margin-top: 1rem;">Exportar CSV</button>
            </div>
            
            <!-- Certificates Link -->
            <div class="admin-content" id="certificates-content">
                <h3>Enlace de Certificados</h3>
                <p>Configure el enlace para que los asistentes puedan descargar sus certificados a partir del 27 de Octubre 2025, 8:00</p>
                
                <div class="certificate-template">
                    <h4>Enlace de Descarga de Certificados</h4>
                    <div class="form-group">
                        <label for="certificate-link">URL de Certificados</label>
                        <input type="url" id="certificate-link" placeholder="https://..." style="width: 100%;">
                    </div>
                    <button id="save-certificate-link" class="btn btn-success">Guardar Enlace</button>
                    <div id="certificate-link-status" style="margin-top: 1rem;"></div>
                </div>
                
                <div style="margin-top: 2rem;">
                    <h4>Información para Participantes</h4>
                    <p>Los certificados estarán disponibles a partir del <strong>27 de Octubre 2025, 8:00</strong>.</p>
                    <p>Los participantes podrán acceder a sus certificados mediante el enlace proporcionado.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Login Modal -->
    <div class="modal" id="login-modal">
        <div class="modal-content">
            <div class="modal-header">
                <span class="close-modal">&times;</span>
                <h2>Acceso Administrativo</h2>
            </div>
            <form id="login-form">
                <div class="form-group">
                    <label for="username">Usuario</label>
                    <input type="text" id="username" name="username" required>
                </div>
                <div class="form-group">
                    <label for="password">Contraseña</label>
                    <input type="password" id="password" name="password" required>
                </div>
                <button type="submit" class="submit-btn">Iniciar Sesión</button>
            </form>
        </div>
    </div>

    <!-- Edit Participant Modal -->
    <div class="edit-modal" id="edit-participant-modal">
        <div class="edit-modal-content">
            <div class="modal-header">
                <span class="close-edit-modal">&times;</span>
                <h2>Editar Participante</h2>
            </div>
            <form id="edit-participant-form">
                <input type="hidden" id="edit-participant-id">
                <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;">
                    <div class="form-group">
                        <label for="edit-cedula">Cedula</label>
                        <input type="text" id="edit-cedula" name="cedula">
                    </div>
                    <div class="form-group">
                        <label for="edit-cargo">Cargo</label>
                        <select id="edit-cargo" name="cargo" required>
                            <option value="DR.">DR.</option>
                            <option value="DRA.">DRA.</option>
                            <option value="LCDO.">LCDO.</option>
                            <option value="LCDA.">LCDA.</option>
                            <option value="IRM.">IRM.</option>
                            <option value="IRE.">IRE.</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="edit-categoria">Categoría</label>
                        <select id="edit-categoria" name="categoria" required>
                            <option value="Médico General">Médico General</option>
                            <option value="Especialista">Especialista</option>
                            <option value="Otro">Otro</option>
                        </select>
                    </div>
                </div>
                <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;">
                    <div class="form-group">
                        <label for="edit-nombre">Nombre</label>
                        <input type="text" id="edit-nombre" name="nombre" required>
                    </div>
                    <div class="form-group">
                        <label for="edit-apellido">Apellido</label>
                        <input type="text" id="edit-apellido" name="apellido" required>
                    </div>
                </div>
                <div class="form-group">
                    <label for="edit-email">Email</label>
                    <input type="email" id="edit-email" name="email" required>
                </div>
                <div class="form-group">
                    <label for="edit-tipo-registro">Tipo de Registro</label>
                    <select id="edit-tipo-registro" name="tipo_registro" required>
                        <option value="publico">Público</option>
                        <option value="preasignado">Preasignado</option>
                    </select>
                </div>
                <button type="submit" class="btn btn-primary">Guardar Cambios</button>
            </form>
        </div>
    </div>

    <!-- Edit Attendance Modal -->
    <div class="edit-modal" id="edit-attendance-modal">
        <div class="edit-modal-content">
            <div class="modal-header">
                <span class="close-edit-attendance-modal">&times;</span>
                <h2>Editar Asistencias</h2>
            </div>
            <form id="edit-attendance-form">
                <input type="hidden" id="edit-attendance-participant-id">
                <div class="form-group">
                    <label><strong>Participante:</strong> <span id="edit-attendance-participant-name"></span></label>
                </div>
                <div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1rem; margin-bottom: 1.5rem;">
                    <div class="form-group">
                        <label>
                            <input type="checkbox" id="edit-attendance-23" value="23">
                            Jueves 23
                        </label>
                    </div>
                    <div class="form-group">
                        <label>
                            <input type="checkbox" id="edit-attendance-24" value="24">
                            Viernes 24
                        </label>
                    </div>
                    <div class="form-group">
                        <label>
                            <input type="checkbox" id="edit-attendance-25" value="25">
                            Sábado 25
                        </label>
                    </div>
                </div>
                <button type="submit" class="btn btn-primary">Guardar Asistencias</button>
            </form>
        </div>
    </div>

    <script>
        // Supabase Configuration - CORREGIDO
        const SUPABASE_URL = 'https://aimghochttwwjceoqtxv.supabase.co';
        const SUPABASE_ANON_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImFpbWdob2NodHR3d2pjZW9xdHh2Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjA3MTkzMjksImV4cCI6MjA3NjI5NTMyOX0.ybudiBx6xCVp8dy21ELm6s17FWMdmGlOnVLSAcPkdWU';
        
        // Initialize Supabase client
        const supabase = window.supabase.createClient(SUPABASE_URL, SUPABASE_ANON_KEY);

        // Global variables
        let participants = [];
        let attendanceData = {};
        let formLinks = {};
        let certificateLink = "";
        let adminLoggedIn = false;
        const registrationDeadline = new Date('2025-10-22T23:59:00');
        const certificatesAvailableDate = new Date('2025-10-27T08:00:00');
        const totalSlots = 220;
        const publicSlots = 50;
        const preassignedSlots = 170;
        
        // DOM Elements
        const countdownElement = document.getElementById('countdown');
        const availableSlotsElement = document.getElementById('available-slots');
        const adminCapacityInfo = document.getElementById('admin-capacity-info');
        const registrationForm = document.getElementById('registration-form');
        const submitBtn = document.getElementById('submit-btn');
        const registrationMessage = document.getElementById('registration-message');
        const adminLoginBtn = document.getElementById('admin-login-btn');
        const adminPanel = document.getElementById('admin-panel');
        const adminLogout = document.getElementById('admin-logout');
        const loginModal = document.getElementById('login-modal');
        const closeModal = document.querySelector('.close-modal');
        const loginForm = document.getElementById('login-form');
        const adminTabs = document.querySelectorAll('.admin-tab');
        const adminContents = document.querySelectorAll('.admin-content');
        const adminRegistrationForm = document.getElementById('admin-registration-form');
        const participantsTableBody = document.getElementById('participants-table-body');
        const searchParticipants = document.getElementById('search-participants');
        const filterCargo = document.getElementById('filter-cargo');
        const filterCategoria = document.getElementById('filter-categoria');
        const filterTipoRegistro = document.getElementById('filter-tipo-registro');
        const exportCsvBtn = document.getElementById('export-csv');
        const attendanceTableBody = document.getElementById('attendance-table-body');
        const searchAttendance = document.getElementById('search-attendance');
        const filterAttendanceStatus = document.getElementById('filter-attendance-status');
        const exportAttendanceBtn = document.getElementById('export-attendance');
        const totalParticipantsElement = document.getElementById('total-participants');
        const approvedParticipantsElement = document.getElementById('approved-participants');
        const pendingParticipantsElement = document.getElementById('pending-participants');
        const totalSlotsElement = document.getElementById('total-slots');
        const assignedSlotsElement = document.getElementById('assigned-slots');
        const publicAvailableSlotsElement = document.getElementById('public-available-slots');
        const preassignedUsedSlotsElement = document.getElementById('preassigned-used-slots');
        const editParticipantModal = document.getElementById('edit-participant-modal');
        const closeEditModal = document.querySelector('.close-edit-modal');
        const editParticipantForm = document.getElementById('edit-participant-form');
        const editAttendanceModal = document.getElementById('edit-attendance-modal');
        const closeEditAttendanceModal = document.querySelector('.close-edit-attendance-modal');
        const editAttendanceForm = document.getElementById('edit-attendance-form');
        const certificateLinkInput = document.getElementById('certificate-link');
        const saveCertificateLinkBtn = document.getElementById('save-certificate-link');
        const certificateLinkStatus = document.getElementById('certificate-link-status');
        
        // Initialize the application
        async function init() {
            console.log("Inicializando aplicación...");
            updateCountdown();
            setInterval(updateCountdown, 1000);
            
            await loadParticipants();
            await loadFormLinks();
            await loadCertificateLink();
            updateAvailableSlots();
            updateRegistrationButton();
            
            // Event listeners
            registrationForm.addEventListener('submit', handleRegistration);
            adminLoginBtn.addEventListener('click', showLoginModal);
            closeModal.addEventListener('click', hideLoginModal);
            loginForm.addEventListener('submit', handleAdminLogin);
            adminLogout.addEventListener('click', handleAdminLogout);
            
            // Admin tab switching
            adminTabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    const tabId = tab.getAttribute('data-tab');
                    switchAdminTab(tabId);
                });
            });
            
            // Admin registration form
            adminRegistrationForm.addEventListener('submit', handleAdminRegistration);
            
            // Search and filter participants
            searchParticipants.addEventListener('input', filterParticipants);
            filterCargo.addEventListener('change', filterParticipants);
            filterCategoria.addEventListener('change', filterParticipants);
            filterTipoRegistro.addEventListener('change', filterParticipants);
            
            // Search and filter attendance
            searchAttendance.addEventListener('input', filterAttendance);
            filterAttendanceStatus.addEventListener('change', filterAttendance);
            
            // Export CSV
            exportCsvBtn.addEventListener('click', exportParticipantsToCSV);
            
            // Certificate link
            saveCertificateLinkBtn.addEventListener('click', saveCertificateLink);
            
            // Attendance form links
            document.querySelectorAll('.attendance-form .btn-primary').forEach(btn => {
                btn.addEventListener('click', function() {
                    const day = this.getAttribute('data-day');
                    saveFormLink(day);
                });
            });
            
            document.querySelectorAll('.attendance-form .btn-success').forEach(btn => {
                btn.addEventListener('click', function() {
                    const day = this.getAttribute('data-day');
                    syncAttendance(day);
                });
            });
            
            // Export attendance
            exportAttendanceBtn.addEventListener('click', exportAttendanceToCSV);
            
            // Edit modals
            closeEditModal.addEventListener('click', () => editParticipantModal.style.display = 'none');
            closeEditAttendanceModal.addEventListener('click', () => editAttendanceModal.style.display = 'none');
            editParticipantForm.addEventListener('submit', handleEditParticipant);
            editAttendanceForm.addEventListener('submit', handleEditAttendance);
            
            // Check if admin is already logged in
            checkAdminSession();
            
            console.log("Aplicación inicializada. Participantes cargados:", participants.length);
        }
        
        // Countdown timer
        function updateCountdown() {
            const now = new Date();
            const targetDate = new Date('2025-10-23T08:00:00');
            const timeRemaining = targetDate - now;
            
            if (timeRemaining <= 0) {
                countdownElement.innerHTML = "¡El congreso ha comenzado!";
                return;
            }
            
            const days = Math.floor(timeRemaining / (1000 * 60 * 60 * 24));
            const hours = Math.floor((timeRemaining % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((timeRemaining % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((timeRemaining % (1000 * 60)) / 1000);
            
            document.getElementById('days').textContent = days.toString().padStart(2, '0');
            document.getElementById('hours').textContent = hours.toString().padStart(2, '0');
            document.getElementById('minutes').textContent = minutes.toString().padStart(2, '0');
            document.getElementById('seconds').textContent = seconds.toString().padStart(2, '0');
        }
        
        // Update available slots display
        function updateAvailableSlots() {
            const publicParticipants = participants.filter(p => 
                p.tipo_registro === 'publico' &&
                (p.cargo === 'DR.' || p.cargo === 'DRA.') && 
                (p.categoria === 'Médico General' || p.categoria === 'Especialista')
            ).length;
            
            const preassignedParticipants = participants.filter(p => 
                p.tipo_registro === 'preasignado'
            ).length;
            
            const availablePublic = Math.max(0, publicSlots - publicParticipants);
            
            // Solo mostrar información detallada para administradores
            if (adminLoggedIn) {
                adminCapacityInfo.style.display = 'block';
                availableSlotsElement.textContent = availablePublic;
            } else {
                adminCapacityInfo.style.display = 'none';
            }
            
            // Actualizar también en el panel administrativo
            const assigned = participants.length;
            
            totalSlotsElement.textContent = totalSlots;
            assignedSlotsElement.textContent = assigned;
            publicAvailableSlotsElement.textContent = availablePublic;
            preassignedUsedSlotsElement.textContent = preassignedParticipants;
        }
        
        // Update registration button based on date and availability
        function updateRegistrationButton() {
            const now = new Date();
            const publicParticipants = participants.filter(p => 
                p.tipo_registro === 'publico' &&
                (p.cargo === 'DR.' || p.cargo === 'DRA.') && 
                (p.categoria === 'Médico General' || p.categoria === 'Especialista')
            ).length;
            
            if (now > registrationDeadline) {
                submitBtn.textContent = 'Inscripciones Cerradas';
                submitBtn.disabled = true;
            } else if (publicParticipants >= publicSlots) {
                submitBtn.textContent = 'No Disponible';
                submitBtn.disabled = true;
            } else {
                submitBtn.textContent = 'Registrarse';
                submitBtn.disabled = false;
            }
        }
        
        // Handle public registration
        async function handleRegistration(e) {
            e.preventDefault();
            
            const formData = new FormData(registrationForm);
            const cargo = formData.get('cargo');
            const nombre = formData.get('nombre');
            const apellido = formData.get('apellido');
            const email = formData.get('email');
            const categoria = formData.get('categoria');
            
            // Check if registration is still open
            const now = new Date();
            if (now > registrationDeadline) {
                showMessage('Las inscripciones han cerrado.', 'error');
                return;
            }
            
            // Check for duplicate email
            if (participants.some(p => p.email === email)) {
                showMessage('Este email ya está registrado.', 'error');
                return;
            }
            
            // Check for duplicate name
            if (participants.some(p => p.nombre === nombre && p.apellido === apellido)) {
                showMessage('Este nombre ya está registrado.', 'error');
                return;
            }
            
            // Check category restrictions - solo DR./DRA. en categorías específicas
            if ((cargo === 'DR.' || cargo === 'DRA.') && 
                (categoria === 'Médico General' || categoria === 'Especialista')) {
                
                const publicParticipants = participants.filter(p => 
                    p.tipo_registro === 'publico' &&
                    (p.cargo === 'DR.' || p.cargo === 'DRA.') && 
                    (p.categoria === 'Médico General' || p.categoria === 'Especialista')
                ).length;
                
                if (publicParticipants >= publicSlots) {
                    showMessage('No hay cupos disponibles para DR./DRA. en este momento.', 'error');
                    return;
                }
            } else {
                showMessage('No hay disponibilidad para esta categoría en este momento.', 'error');
                return;
            }
            
            // Add participant to Supabase
            const { data, error } = await supabase
                .from('participants')
                .insert([
                    { 
                        cargo, 
                        nombre, 
                        apellido, 
                        email, 
                        categoria,
                        tipo_registro: 'publico',
                        fecha_registro: new Date().toISOString()
                    }
                ])
                .select();
            
            if (error) {
                console.error('Error al registrar participante:', error);
                showMessage('Error al registrar. Intente nuevamente.', 'error');
                return;
            }
            
            // Add participant to local array
            const newParticipant = {
                id: data[0].id,
                cargo,
                nombre,
                apellido,
                email,
                categoria,
                tipo_registro: 'publico',
                fecha_registro: new Date().toISOString()
            };
            
            participants.push(newParticipant);
            updateAvailableSlots();
            updateRegistrationButton();
            updateAttendanceDashboard();
            
            showMessage('¡Registro exitoso! Te esperamos en el congreso.', 'success');
            registrationForm.reset();
        }
        
        // Show message to user
        function showMessage(message, type) {
            registrationMessage.textContent = message;
            registrationMessage.style.color = type === 'success' ? 'green' : 'red';
            registrationMessage.style.fontWeight = '600';
            
            setTimeout(() => {
                registrationMessage.textContent = '';
            }, 5000);
        }
        
        // Admin functions
        function showLoginModal() {
            loginModal.style.display = 'flex';
        }
        
        function hideLoginModal() {
            loginModal.style.display = 'none';
            loginForm.reset();
        }
        
        function handleAdminLogin(e) {
            e.preventDefault();
            
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            if (username === 'DOCENCIA' && password === 'DOCENCIA') {
                adminLoggedIn = true;
                sessionStorage.setItem('adminLoggedIn', 'true');
                sessionStorage.setItem('loginTime', new Date().getTime().toString());
                
                adminPanel.style.display = 'block';
                hideLoginModal();
                updateAdminDashboard();
                
                // Mostrar información de cupos para administradores
                adminCapacityInfo.style.display = 'block';
                
                // Set session timeout (8 hours)
                setTimeout(() => {
                    handleAdminLogout();
                }, 8 * 60 * 60 * 1000);
            } else {
                alert('Credenciales incorrectas. Intente nuevamente.');
            }
        }
        
        function checkAdminSession() {
            const loggedIn = sessionStorage.getItem('adminLoggedIn');
            const loginTime = parseInt(sessionStorage.getItem('loginTime') || '0');
            const now = new Date().getTime();
            
            // Check if session is still valid (8 hours)
            if (loggedIn === 'true' && (now - loginTime) < (8 * 60 * 60 * 1000)) {
                adminLoggedIn = true;
                adminPanel.style.display = 'block';
                updateAdminDashboard();
                
                // Mostrar información de cupos para administradores
                adminCapacityInfo.style.display = 'block';
                
                // Reset timeout
                setTimeout(() => {
                    handleAdminLogout();
                }, 8 * 60 * 60 * 1000 - (now - loginTime));
            }
        }
        
        function handleAdminLogout() {
            adminLoggedIn = false;
            sessionStorage.removeItem('adminLoggedIn');
            sessionStorage.removeItem('loginTime');
            
            adminPanel.style.display = 'none';
            // Ocultar información de cupos para usuarios normales
            adminCapacityInfo.style.display = 'none';
            alert('Sesión cerrada exitosamente.');
        }
        
        function switchAdminTab(tabId) {
            // Update active tab
            adminTabs.forEach(tab => {
                if (tab.getAttribute('data-tab') === tabId) {
                    tab.classList.add('active');
                } else {
                    tab.classList.remove('active');
                }
            });
            
            // Update active content
            adminContents.forEach(content => {
                if (content.id === `${tabId}-content`) {
                    content.classList.add('active');
                } else {
                    content.classList.remove('active');
                }
            });
            
            // Load specific data if needed
            if (tabId === 'attendance') {
                updateAttendanceDashboard();
            }
        }
        
        async function handleAdminRegistration(e) {
            e.preventDefault();
            
            const formData = new FormData(adminRegistrationForm);
            const cargo = formData.get('cargo');
            const nombre = formData.get('nombre');
            const apellido = formData.get('apellido');
            const email = formData.get('email');
            const categoria = formData.get('categoria');
            const tipo_registro = formData.get('tipo_registro');
            
            // Check for duplicate email
            if (participants.some(p => p.email === email)) {
                alert('Este email ya está registrado.');
                return;
            }
            
            // Check for duplicate name
            if (participants.some(p => p.nombre === nombre && p.apellido === apellido)) {
                alert('Este nombre ya está registrado.');
                return;
            }
            
            // Add participant to Supabase
            const { data, error } = await supabase
                .from('participants')
                .insert([
                    { 
                        cargo, 
                        nombre, 
                        apellido, 
                        email, 
                        categoria,
                        tipo_registro,
                        fecha_registro: new Date().toISOString()
                    }
                ])
                .select();
            
            if (error) {
                console.error('Error al registrar participante:', error);
                alert('Error al registrar participante. Intente nuevamente.');
                return;
            }
            
            // Add participant to local array
            const newParticipant = {
                id: data[0].id,
                cargo,
                nombre,
                apellido,
                email,
                categoria,
                tipo_registro,
                fecha_registro: new Date().toISOString()
            };
            
            participants.push(newParticipant);
            updateAvailableSlots();
            updateRegistrationButton();
            updateAdminDashboard();
            updateAttendanceDashboard();
            
            alert('Participante registrado exitosamente.');
            adminRegistrationForm.reset();
        }
        
        function updateAdminDashboard() {
            // Update stats
            const assigned = participants.length;
            const publicParticipants = participants.filter(p => 
                p.tipo_registro === 'publico' &&
                (p.cargo === 'DR.' || p.cargo === 'DRA.') && 
                (p.categoria === 'Médico General' || p.categoria === 'Especialista')
            ).length;
            
            const preassignedParticipants = participants.filter(p => 
                p.tipo_registro === 'preasignado'
            ).length;
            
            const availablePublic = Math.max(0, publicSlots - publicParticipants);
            
            totalSlotsElement.textContent = totalSlots;
            assignedSlotsElement.textContent = assigned;
            publicAvailableSlotsElement.textContent = availablePublic;
            preassignedUsedSlotsElement.textContent = preassignedParticipants;
            
            // Update participants table
            renderParticipantsTable();
        }
        
        function renderParticipantsTable(filteredParticipants = null) {
            const participantsToShow = filteredParticipants || participants;
            
            participantsTableBody.innerHTML = '';
            
            if (participantsToShow.length === 0) {
                participantsTableBody.innerHTML = '<tr><td colspan="6" style="text-align: center;">No hay participantes registrados</td></tr>';
                return;
            }
            
            participantsToShow.forEach(participant => {
                const row = document.createElement('tr');
                
                row.innerHTML = `
                   <td>${participant.cedula}</td>
                    <td>${participant.cargo} ${participant.nombre} ${participant.apellido}</td>
                    <td>${participant.email}</td>
                    <td>${participant.cargo}</td>
                    <td>${participant.categoria}</td>
                    <td>${participant.tipo_registro === 'publico' ? 'Público' : 'Preasignado'}</td>
                    <td class="action-buttons">
                        <button class="btn btn-warning" onclick="editParticipant('${participant.id}')">Editar</button>
                        <button class="btn btn-danger" onclick="deleteParticipant('${participant.id}')">Eliminar</button>
                    </td>
                `;
                
                participantsTableBody.appendChild(row);
            });
        }
        
        function filterParticipants() {
            const searchTerm = searchParticipants.value.toLowerCase();
            const cargoFilter = filterCargo.value;
            const categoriaFilter = filterCategoria.value;
            const tipoRegistroFilter = filterTipoRegistro.value;
            
            const filtered = participants.filter(p => {
                const matchesSearch = 
                    p.nombre.toLowerCase().includes(searchTerm) ||
                    p.apellido.toLowerCase().includes(searchTerm) ||
                    p.email.toLowerCase().includes(searchTerm) ||
                    p.cargo.toLowerCase().includes(searchTerm);
                
                const matchesCargo = !cargoFilter || p.cargo === cargoFilter;
                const matchesCategoria = !categoriaFilter || p.categoria === categoriaFilter;
                const matchesTipoRegistro = !tipoRegistroFilter || p.tipo_registro === tipoRegistroFilter;
                
                return matchesSearch && matchesCargo && matchesCategoria && matchesTipoRegistro;
            });
            
            renderParticipantsTable(filtered);
        }
        
        function editParticipant(id) {
            const participant = participants.find(p => p.id === id);
            if (!participant) return;
            
            document.getElementById('edit-participant-id').value = participant.id;
            document.getElementById('edit-cargo').value = participant.cargo;
            document.getElementById('edit-categoria').value = participant.categoria;
            document.getElementById('edit-nombre').value = participant.nombre;
            document.getElementById('edit-apellido').value = participant.apellido;
            document.getElementById('edit-email').value = participant.email;
            document.getElementById('edit-tipo-registro').value = participant.tipo_registro;
            
            editParticipantModal.style.display = 'flex';
        }
        
        async function handleEditParticipant(e) {
            e.preventDefault();
            
            const id = document.getElementById('edit-participant-id').value;
            const cargo = document.getElementById('edit-cargo').value;
            const nombre = document.getElementById('edit-nombre').value;
            const apellido = document.getElementById('edit-apellido').value;
            const email = document.getElementById('edit-email').value;
            const categoria = document.getElementById('edit-categoria').value;
            const tipo_registro = document.getElementById('edit-tipo-registro').value;
            const cedula = document.getElementById('edit-apellido').value;
            
            const participantIndex = participants.findIndex(p => p.id === id);
            if (participantIndex === -1) return;
            
            // Check for duplicate email (excluding current participant)
            if (participants.some(p => p.id !== id && p.email === email)) {
                alert('Este email ya está registrado por otro participante.');
                return;
            }
            
            // Check for duplicate name (excluding current participant)
            if (participants.some(p => p.id !== id && p.nombre === nombre && p.apellido === apellido)) {
                alert('Este nombre ya está registrado por otro participante.');
                return;
            }
            
            // Update participant in Supabase
            const { error } = await supabase
                .from('participants')
                .update({ cargo, nombre, apellido, email, categoria, tipo_registro,cedula })
                .eq('id', id);
            
            if (error) {
                console.error('Error al actualizar participante:', error);
                alert('Error al actualizar participante. Intente nuevamente.');
                return;
            }
            
            // Update participant in local array
            participants[participantIndex] = {
                ...participants[participantIndex],
                cargo,
                nombre,
                apellido,
                email,
                categoria,
                tipo_registro
            };
            
            updateAvailableSlots();
            updateRegistrationButton();
            updateAdminDashboard();
            updateAttendanceDashboard();
            
            editParticipantModal.style.display = 'none';
            alert('Participante actualizado exitosamente.');
        }
        
        async function deleteParticipant(id) {
            if (confirm('¿Está seguro de que desea eliminar este participante?')) {
                // Delete participant from Supabase
                const { error } = await supabase
                    .from('participants')
                    .delete()
                    .eq('id', id);
                
                if (error) {
                    console.error('Error al eliminar participante:', error);
                    alert('Error al eliminar participante. Intente nuevamente.');
                    return;
                }
                
                // Delete participant from local array
                participants = participants.filter(p => p.id !== id);
                updateAvailableSlots();
                updateRegistrationButton();
                updateAdminDashboard();
                updateAttendanceDashboard();
            }
        }
        
        function exportParticipantsToCSV() {
            if (participants.length === 0) {
                alert('No hay datos para exportar.');
                return;
            }
            
            let csvContent = 'Cargo,Nombre,Apellido,Email,Categoría,Tipo Registro,Fecha Registro\n';
            
            participants.forEach(p => {
                csvContent += `"${p.cargo}","${p.nombre}","${p.apellido}","${p.email}","${p.categoria}","${p.tipo_registro}","${p.fecha_registro}"\n`;
            });
            
            const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
            saveAs(blob, 'participantes_congreso.csv');
        }
        
        // Form links management
        async function saveFormLink(day) {
            const linkInput = document.getElementById(`form-link-${day}`);
            const link = linkInput.value.trim();
            
            if (!link) {
                alert('Por favor, ingrese un enlace válido.');
                return;
            }
            
            // Validate URL format
            try {
                new URL(link);
            } catch (e) {
                alert('Por favor, ingrese un enlace válido.');
                return;
            }
            
            // Save form link to Supabase
            const { error } = await supabase
                .from('config')
                .upsert({ key: `form_link_${day}`, value: link });
            
            if (error) {
                console.error('Error al guardar enlace:', error);
                alert('Error al guardar enlace. Intente nuevamente.');
                return;
            }
            
            // Save form link locally
            formLinks[day] = link;
            
            alert(`Enlace para el día ${day} guardado exitosamente.`);
        }
        
        async function syncAttendance(day) {
            const link = formLinks[day];
            if (!link) {
                alert('Primero debe guardar un enlace para este día.');
                return;
            }
            
            // Simulate synchronization
            alert(`Sincronizando asistencias para el día ${day} desde: ${link}`);
            
            // Simulate fetching data and updating attendance
            if (!attendanceData[day]) {
                attendanceData[day] = {};
            }
            
            // Mark some random participants as attended
            participants.forEach(p => {
                if (Math.random() > 0.3) {
                    attendanceData[day][p.id] = true;
                }
            });
            
            // Save attendance data to Supabase
            for (const participantId in attendanceData[day]) {
                if (attendanceData[day][participantId]) {
                    const { error } = await supabase
                        .from('attendance')
                        .upsert({ 
                            participant_id: participantId, 
                            day: parseInt(day), 
                            attended: true 
                        });
                    
                    if (error) {
                        console.error('Error al guardar asistencia:', error);
                    }
                }
            }
            
            updateAttendanceDashboard();
            alert(`Asistencias sincronizadas para el día ${day}.`);
        }
        
        async function loadFormLinks() {
            // Load form links from Supabase
            const { data, error } = await supabase
                .from('config')
                .select('key, value')
                .like('key', 'form_link_%');
            
            if (error) {
                console.error('Error al cargar enlaces de formularios:', error);
                return;
            }
            
            if (data && data.length > 0) {
                data.forEach(item => {
                    const day = item.key.replace('form_link_', '');
                    formLinks[day] = item.value;
                    
                    // Populate form fields
                    const input = document.getElementById(`form-link-${day}`);
                    if (input) {
                        input.value = item.value;
                    }
                });
            } else {
                // Set default links
                formLinks = {
                    '23': 'https://docs.google.com/forms/d/1nihA_9JrKg1KOJCy4ypah4wtS5wXN3ETaKDgxNjTj70/edit#responses',
                    '24': 'https://docs.google.com/forms/d/18n4OUSB3iGBlBTBH6k4d-Tvma1rSXSS0Yv_vdq7bLVY/edit#responses',
                    '25': 'https://docs.google.com/forms/d/11PXiisbAVSnWc74sRQJntSvnbSFk53um0CQikR0QHww/edit?edit_requested=true#responses'
                };
                
                // Populate form fields with default links
                document.getElementById('form-link-23').value = formLinks['23'];
                document.getElementById('form-link-24').value = formLinks['24'];
                document.getElementById('form-link-25').value = formLinks['25'];
                
                // Save default links to Supabase
                for (const day in formLinks) {
                    await supabase
                        .from('config')
                        .upsert({ key: `form_link_${day}`, value: formLinks[day] });
                }
            }
        }
        
        // Certificate link management
        async function saveCertificateLink() {
            const link = certificateLinkInput.value.trim();
            
            if (!link) {
                alert('Por favor, ingrese un enlace válido.');
                return;
            }
            
            // Validate URL format
            try {
                new URL(link);
            } catch (e) {
                alert('Por favor, ingrese un enlace válido.');
                return;
            }
            
            // Save certificate link to Supabase
            const { error } = await supabase
                .from('config')
                .upsert({ key: 'certificate_link', value: link });
            
            if (error) {
                console.error('Error al guardar enlace de certificados:', error);
                alert('Error al guardar enlace. Intente nuevamente.');
                return;
            }
            
            // Save certificate link locally
            certificateLink = link;
            
            certificateLinkStatus.innerHTML = `<p style="color: var(--success-green);"><i class="fas fa-check-circle"></i> Enlace guardado exitosamente.</p>`;
            alert('Enlace de certificados guardado exitosamente.');
        }
        
        async function loadCertificateLink() {
            // Load certificate link from Supabase
            const { data, error } = await supabase
                .from('config')
                .select('value')
                .eq('key', 'certificate_link')
                .single();
            
            if (error && error.code !== 'PGRST116') {
                console.error('Error al cargar enlace de certificados:', error);
                return;
            }
            
            if (data) {
                certificateLink = data.value;
                certificateLinkInput.value = certificateLink;
            }
        }
        
        // Attendance management
        async function updateAttendanceDashboard() {
            // Load attendance data from Supabase
            const { data, error } = await supabase
                .from('attendance')
                .select('*');
            
            if (error) {
                console.error('Error al cargar datos de asistencia:', error);
                return;
            }
            
            // Reset attendance data
            attendanceData = {};
            
            // Process attendance data
            if (data) {
                data.forEach(record => {
                    if (!attendanceData[record.day]) {
                        attendanceData[record.day] = {};
                    }
                    attendanceData[record.day][record.participant_id] = record.attended;
                });
            }
            
            // Calculate attendance statistics
            const total = participants.length;
            let approved = 0;
            let pending = 0;
            
            participants.forEach(p => {
                const daysAttended = getParticipantAttendances(p.id);
                if (daysAttended >= 2) {
                    approved++;
                } else {
                    pending++;
                }
            });
            
            totalParticipantsElement.textContent = total;
            approvedParticipantsElement.textContent = approved;
            pendingParticipantsElement.textContent = pending;
            
            // Update attendance table
            renderAttendanceTable();
        }
        
        function renderAttendanceTable(filteredParticipants = null) {
            const participantsToShow = filteredParticipants || participants;
            
            attendanceTableBody.innerHTML = '';
            
            if (participantsToShow.length === 0) {
                attendanceTableBody.innerHTML = '<tr><td colspan="6" style="text-align: center;">No hay participantes registrados</td></tr>';
                return;
            }
            
            participantsToShow.forEach(participant => {
                const row = document.createElement('tr');
                
                const day23 = attendanceData['23'] && attendanceData['23'][participant.id] ? '✓' : '✗';
                const day24 = attendanceData['24'] && attendanceData['24'][participant.id] ? '✓' : '✗';
                const day25 = attendanceData['25'] && attendanceData['25'][participant.id] ? '✓' : '✗';
                
                const daysAttended = [day23, day24, day25].filter(d => d === '✓').length;
                const status = daysAttended >= 2 ? 'Aprobado' : 'No Aprobado';
                
                row.innerHTML = `
                    <td>${participant.cargo} ${participant.nombre} ${participant.apellido}</td>
                    <td>${day23}</td>
                    <td>${day24}</td>
                    <td>${day25}</td>
                    <td>${status}</td>
                    <td class="action-buttons">
                        <button class="btn btn-warning" onclick="editAttendance('${participant.id}')">Editar</button>
                    </td>
                `;
                
                attendanceTableBody.appendChild(row);
            });
        }
        
        function filterAttendance() {
            const searchTerm = searchAttendance.value.toLowerCase();
            const statusFilter = filterAttendanceStatus.value;
            
            const filtered = participants.filter(p => {
                const matchesSearch = 
                    p.nombre.toLowerCase().includes(searchTerm) ||
                    p.apellido.toLowerCase().includes(searchTerm) ||
                    p.cargo.toLowerCase().includes(searchTerm);
                
                const attendances = getParticipantAttendances(p.id);
                const status = attendances >= 2 ? 'Aprobado' : 'No Aprobado';
                const matchesStatus = !statusFilter || status === statusFilter;
                
                return matchesSearch && matchesStatus;
            });
            
            renderAttendanceTable(filtered);
        }
        
        function editAttendance(participantId) {
            const participant = participants.find(p => p.id === participantId);
            if (!participant) return;
            
            document.getElementById('edit-attendance-participant-id').value = participant.id;
            document.getElementById('edit-attendance-participant-name').textContent = 
                `${participant.cargo} ${participant.nombre} ${participant.apellido}`;
            
            // Set checkbox values based on current attendance
            document.getElementById('edit-attendance-23').checked = 
                attendanceData['23'] && attendanceData['23'][participant.id] || false;
            document.getElementById('edit-attendance-24').checked = 
                attendanceData['24'] && attendanceData['24'][participant.id] || false;
            document.getElementById('edit-attendance-25').checked = 
                attendanceData['25'] && attendanceData['25'][participant.id] || false;
            
            editAttendanceModal.style.display = 'flex';
        }
        
        async function handleEditAttendance(e) {
            e.preventDefault();
            
            const participantId = document.getElementById('edit-attendance-participant-id').value;
            const day23 = document.getElementById('edit-attendance-23').checked;
            const day24 = document.getElementById('edit-attendance-24').checked;
            const day25 = document.getElementById('edit-attendance-25').checked;
            
            // Update attendance data in Supabase
            const updates = [];
            
            if (day23) {
                updates.push(
                    supabase.from('attendance')
                        .upsert({ participant_id: participantId, day: 23, attended: true })
                );
            } else {
                updates.push(
                    supabase.from('attendance')
                        .delete()
                        .eq('participant_id', participantId)
                        .eq('day', 23)
                );
            }
            
            if (day24) {
                updates.push(
                    supabase.from('attendance')
                        .upsert({ participant_id: participantId, day: 24, attended: true })
                );
            } else {
                updates.push(
                    supabase.from('attendance')
                        .delete()
                        .eq('participant_id', participantId)
                        .eq('day', 24)
                );
            }
            
            if (day25) {
                updates.push(
                    supabase.from('attendance')
                        .upsert({ participant_id: participantId, day: 25, attended: true })
                );
            } else {
                updates.push(
                    supabase.from('attendance')
                        .delete()
                        .eq('participant_id', participantId)
                        .eq('day', 25)
                );
            }
            
            // Execute all updates
            const results = await Promise.all(updates);
            
            // Check for errors
            for (const result of results) {
                if (result.error) {
                    console.error('Error al actualizar asistencia:', result.error);
                    alert('Error al actualizar asistencias. Intente nuevamente.');
                    return;
                }
            }
            
            // Update attendance data locally
            if (!attendanceData['23']) attendanceData['23'] = {};
            if (!attendanceData['24']) attendanceData['24'] = {};
            if (!attendanceData['25']) attendanceData['25'] = {};
            
            attendanceData['23'][participantId] = day23;
            attendanceData['24'][participantId] = day24;
            attendanceData['25'][participantId] = day25;
            
            updateAttendanceDashboard();
            
            editAttendanceModal.style.display = 'none';
            alert('Asistencias actualizadas exitosamente.');
        }
        
        function exportAttendanceToCSV() {
            if (participants.length === 0) {
                alert('No hay datos para exportar.');
                return;
            }
            
            let csvContent = 'Nombre,Jueves 23,Viernes 24,Sábado 25,Estado\n';
            
            participants.forEach(p => {
                const day23 = attendanceData['23'] && attendanceData['23'][p.id] ? 'Presente' : 'Ausente';
                const day24 = attendanceData['24'] && attendanceData['24'][p.id] ? 'Presente' : 'Ausente';
                const day25 = attendanceData['25'] && attendanceData['25'][p.id] ? 'Presente' : 'Ausente';
                
                const daysAttended = [day23, day24, day25].filter(d => d === 'Presente').length;
                const status = daysAttended >= 2 ? 'Aprobado' : 'No Aprobado';
                
                csvContent += `"${p.cargo} ${p.nombre} ${p.apellido}","${day23}","${day24}","${day25}","${status}"\n`;
            });
            
            const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
            saveAs(blob, 'asistencias_congreso.csv');
        }
        
        // Utility functions
        function getParticipantAttendances(participantId) {
            let count = 0;
            ['23', '24', '25'].forEach(day => {
                if (attendanceData[day] && attendanceData[day][participantId]) {
                    count++;
                }
            });
            return count;
        }
        
        async function loadParticipants() {
            // Load participants from Supabase
            const { data, error } = await supabase
                .from('participants')
                .select('*')
                .order('fecha_registro', { ascending: false });
            
            if (error) {
                console.error('Error al cargar participantes:', error);
                participants = [];
                return;
            }
            
            if (data) {
                participants = data.map(p => ({
                    id: p.id,
                    cargo: p.cargo,
                    nombre: p.nombre,
                    apellido: p.apellido,
                    email: p.email,
                    categoria: p.categoria,
                    tipo_registro: p.tipo_registro,
                    fecha_registro: p.fecha_registro
                }));
                
                console.log("Participantes cargados desde Supabase:", participants.length);
            } else {
                console.log("No hay datos en Supabase, comenzando con lista vacía");
                participants = [];
            }
        }
        
        // Make functions available globally for onclick events
        window.editParticipant = editParticipant;
        window.deleteParticipant = deleteParticipant;
        window.editAttendance = editAttendance;
        
        // Initialize the application when DOM is loaded
        document.addEventListener('DOMContentLoaded', init);
    </script>
</body>
</html>
