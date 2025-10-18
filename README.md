-- Tabla de participantes
CREATE TABLE participants (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  cargo TEXT NOT NULL,
  nombre TEXT NOT NULL,
  apellido TEXT NOT NULL,
  email TEXT NOT NULL UNIQUE,
  categoria TEXT NOT NULL,
  preasignado BOOLEAN DEFAULT FALSE,
  fecha_registro TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Tabla de asistencia
CREATE TABLE attendance (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  participant_id UUID REFERENCES participants(id) ON DELETE CASCADE,
  day INTEGER NOT NULL CHECK (day IN (23, 24, 25)),
  attended BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  UNIQUE(participant_id, day)
);

-- Tabla de configuración
CREATE TABLE config (
  key TEXT PRIMARY KEY,
  value TEXT,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Insertar enlaces de formularios por defecto
INSERT INTO config (key, value) VALUES 
('form_link_23', 'https://docs.google.com/forms/d/1nihA_9JrKg1KOJCy4ypah4wtS5wXN3ETaKDgxNjTj70/edit#responses'),
('form_link_24', 'https://docs.google.com/forms/d/18n4OUSB3iGBlBTBH6k4d-Tvma1rSXSS0Yv_vdq7bLVY/edit#responses'),
('form_link_25', 'https://docs.google.com/forms/d/11PXiisbAVSnWc74sRQJntSvnbSFk53um0CQikR0QHww/edit?edit_requested=true#responses')
ON CONFLICT (key) DO NOTHING;

-- Habilitar RLS (Row Level Security) pero permitir todo para la aplicación
ALTER TABLE participants ENABLE ROW LEVEL SECURITY;
ALTER TABLE attendance ENABLE ROW LEVEL SECURITY;
ALTER TABLE config ENABLE ROW LEVEL SECURITY;

-- Políticas para permitir todas las operaciones (ya que usamos la clave anónima)
CREATE POLICY "Allow all operations on participants" ON participants
FOR ALL USING (true);

CREATE POLICY "Allow all operations on attendance" ON attendance
FOR ALL USING (true);

CREATE POLICY "Allow all operations on config" ON config
FOR ALL USING (true);

-- Índices para mejorar el rendimiento
CREATE INDEX idx_participants_email ON participants(email);
CREATE INDEX idx_participants_cargo ON participants(cargo);
CREATE INDEX idx_participants_categoria ON participants(categoria);
CREATE INDEX idx_attendance_participant_id ON attendance(participant_id);
CREATE INDEX idx_attendance_day ON attendance(day);
