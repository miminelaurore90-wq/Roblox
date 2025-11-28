# Roblox
🚧 Guía Rápida para Crear tu Propio Obby en Roblox Studio¡al mundo de la creación de juegos de Roblox! Un Obby (Obstacle Course o Carrera deBienvenido  Obstáculos) es uno de los juegos más populares para empezar. Esta guía te llevará a través de los pasos esenciales para construir el tuyo.1. Configuración Inicial en Roblox Studio1.1 Abrir un Nuevo ProyectoAbre Roblox Studio.Haz clic en la plantilla "Baseplate" (Plataforma Base) o "Obby" (si buscas una base preconfigurada con checkpoints). Usaremos "Baseplate" para hacerlo desde cero.Asegúrate de tener las pestañas Explorer (Explorador) y Properties (Propiedades) abiertas (Menú View > Explorer y Properties).1.2 Anclar el Punto de Inicio (Spawn Point)Todo juego necesita un lugar donde el jugador comience:En la pestaña Home (Inicio), haz clic en Part (Pieza) y selecciona un bloque.En la pestaña Model (Modelo), asegúrate de que "Anchor" (Anclaje) esté activado para que las partes no se caigan.En la pestaña Home, usa las herramientas Move (Mover), Scale (Escalar) y Rotate (Rotar) para colocar y dimensionar tu bloque de inicio.Añade el Spawn Point: En la pestaña Model, haz clic en Spawn (Punto de Aparición). Colócalo encima de tu bloque de inicio.2. Creación de Obstáculos BásicosUsa la herramienta Part para añadir bloques y luego las herramientas Move y Scale para darles forma.2.1 El Clásico Salto de PlataformasDiseño: Coloca una serie de plataformas simples con espacios que el jugador debe saltar.Tip: Varía la distancia de salto para aumentar la dificultad.2.2 Obstáculo de "Parte Asesina" (Kill Part)Este es un bloque que mata al jugador al tocarlo (como lava o ácido).Crea una nueva Part (por ejemplo, un bloque rojo para simular lava).Asegúrate de que la propiedad Anchored esté activada.Añadir el Script de Muerte:En el panel Explorer, haz clic en el signo + junto a la Part (el bloque rojo).Selecciona Script.Borra el código por defecto y pega el siguiente código Lua:-- Este es el script para la Parte Asesina (Kill Part)
local killPart = script.Parent -- Referencia a la pieza padre (el bloque de lava)

-- Función que se ejecuta cuando algo toca la pieza
local function onPartTouched(otherPart)
    -- Buscamos el Humanoid (el objeto que gestiona la vida del jugador)
    local parentModel = otherPart.Parent
    local humanoid = parentModel:FindFirstChild("Humanoid")

    -- Si encontramos el Humanoid, reducimos su vida a cero
    if humanoid then
        humanoid.Health = 0
    end


-- Conectamos la función al evento 'Touched' (Tocado)
killPart.Touched:Connect(onPartTouched)

