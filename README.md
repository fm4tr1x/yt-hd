# yt-hd
Youtube Downloader 
import os
import pafy

# URL del video.
url = ""
try:
    url = str(input("✏️   Inserta la URL o Playlist a descargar: "))

    # Creamos el objeto para el video.
    video = pafy.new(url)

    # Mostramos información del video.
    print(f"🎵  Título: {video.title}.")
    print(f"🎵  Autor: {video.author}.")
    print(f"🎵  Duración: {video.duration}.")
    print(f"〽️  Rating 0-5: {video.rating}.")
    print(f"👀  Reproducciones: {video.viewcount}.")
    print(f"👍  Likes: {video.likes}.")
    print(f"👎  Dislikes: {video.dislikes}.")
    print(f"🌐  Canal de Youtube: https://www.youtube.com/channel/{video.username}\n")

    # Extraemos información sobre la mejor calidad de video disponible.
    print("🔵  Buscando la mejor calidad de video disponible.")
    print(f"⚪️  {video.videostreams}\n")
    bestResolutionVideo = video.getbest()

    # Descargamos el video.
    print("🟠  Descargando.\n")
    bestResolutionVideo.download()
    print("\n🟢  Descarga guardada en: "+os.getcwd())
    
    # Creamos un log de descargas.
    log = open ("YT-HD.log", "a")
    log.write("\n"+video.title+" || "+url)
    log.close()
    log = open("YT-HD.log")
    log.read()
    log.close()
    print("📝  Añadiendo información de la descarga a YT-HD.log")

# Controlamos los errores.
except ValueError:
    print("🔴  ERROR: URL no válida.")
except KeyboardInterrupt:
    print("\n🔴  Interrumpido por el usuario.")
finally: # Acabamos el programa.
    print("🏴  Saliendo de YT-HD.")
