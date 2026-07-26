```Python
 
      
from sentence_transformers import SentenceTransformer
import numpy as np

documentos = [
    # Tecnología
    "La inteligencia artificial mejora los diagnósticos médicos.",
    "Los algoritmos aprenden patrones a partir de datos.",
    "Python es un lenguaje popular para ciencia de datos.",
    "Las redes neuronales procesan grandes cantidades de información.",
    "La computación en la nube ofrece servicios escalables.",
    "La ciberseguridad protege sistemas informáticos.",
    "Los robots ayudan en tareas industriales.",
    "El aprendizaje profundo impulsa la visión artificial.",
    "Los sensores recopilan información del entorno.",
    "Las bases de datos almacenan información.",
    # Deportes
    "El fútbol es un deporte de equipo.",
    "El baloncesto requiere coordinación.",
    "Los atletas entrenan diariamente.",
    "La natación mejora la resistencia.",
    "El tenis exige precisión.",
    "El ciclismo fortalece las piernas.",
    "El béisbol utiliza bate y pelota.",
    "El voleibol se juega en equipos.",
    "Correr mejora la salud.",
    "El ajedrez desarrolla estrategia.",
    # Música
    "La guitarra es un instrumento musical.",
    "El piano tiene teclas.",
    "La música clásica relaja.",
    "El rock usa guitarras eléctricas.",
    "El jazz destaca por la improvisación.",
    "La batería marca el ritmo.",
    "El violín produce sonidos agudos.",
    "El canto requiere práctica.",
    "Una orquesta reúne muchos músicos.",
    "Las canciones transmiten emociones.",
    # Gastronomía
    "La pizza italiana es famosa.",
    "La pasta lleva diferentes salsas.",
    "El ceviche utiliza pescado.",
    "Las frutas aportan vitaminas.",
    "El café contiene cafeína.",
    "El chocolate proviene del cacao.",
    "Las verduras son saludables.",
    "El pan se hornea.",
    "La sopa se sirve caliente.",
    "El queso acompaña muchas comidas.",
    # Animales
    "Los perros son animales domésticos.",
    "Los gatos cazan ratones.",
    "Las aves vuelan.",
    "Los delfines son mamíferos.",
    "Los leones viven en manadas.",
    "Los caballos son veloces.",
    "Las abejas producen miel.",
    "Los elefantes tienen trompa.",
    "Los peces viven en el agua.",
    "Las tortugas viven muchos años."
]

modelo = SentenceTransformer("paraphrase-multilingual-MiniLM-L12-v2")
emb_docs = modelo.encode(documentos)

while True:
    consulta = input("\nIngrese una consulta: ").strip()
    if not consulta:
        print("Consulta vacía.")
        continue

    emb_q = modelo.encode([consulta])[0]
    norma_q = np.linalg.norm(emb_q)

    resultados = []

    print("\nCÁLCULOS")
    print("="*70)
    for i, emb in enumerate(emb_docs):
        producto = float(np.dot(emb_q, emb))
        norma_d = float(np.linalg.norm(emb))
        coseno = producto / (norma_q * norma_d)

        print(f"\nDocumento {i+1}")
        print(f"Producto punto : {producto:.6f}")
        print(f"Norma consulta : {norma_q:.6f}")
        print(f"Norma documento: {norma_d:.6f}")
        print(f"Similitud      : {coseno:.6f}")

        resultados.append((i, coseno))

    resultados.sort(key=lambda x: x[1], reverse=True)

    print("\nTOP 5")
    print("="*70)
    for pos, (idx, sim) in enumerate(resultados[:5], start=1):
        print(f"{pos}. ({sim:.6f}) {documentos[idx]}")

    mejor = resultados[0]
    print("\nDocumento más relevante:")
    print(documentos[mejor[0]])
    print(f"Similitud: {mejor[1]:.6f}")

    op = input("\n¿Desea realizar otra búsqueda? (S/N): ").strip().lower()
    if op != "s":
        break

```
