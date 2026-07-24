```Python
from sentence_transformers import SentenceTransformer
from sklearn.metrics.pairwise import cosine_similarity
import numpy as np


# ==========================================================
# SISTEMA DE BÚSQUEDA SEMÁNTICA CON EMBEDDINGS
# Modelo: paraphrase-multilingual-MiniLM-L12-v2
# ==========================================================


def cargar_modelo():
    """
    Carga el modelo de Sentence Transformers.
    """
    print("Cargando modelo...\n")
    return SentenceTransformer("paraphrase-multilingual-MiniLM-L12-v2")


def validar_entrada(documentos, consulta):
    """
    Verifica que la entrada sea válida.
    """

    if not documentos:
        raise ValueError("La lista de documentos está vacía.")

    if not consulta:
        raise ValueError("La consulta está vacía.")

    if isinstance(consulta, list):
        if len(consulta) != 1:
            raise ValueError(
                "La consulta debe contener únicamente un elemento."
            )


def generar_embeddings(modelo, documentos, consulta):
    """
    Genera los embeddings de documentos y consulta.
    """

    vectores_docs = modelo.encode(documentos)

    if isinstance(consulta, list):
        vector_consulta = modelo.encode(consulta)
    else:
        vector_consulta = modelo.encode([consulta])

    return vectores_docs, vector_consulta


def mostrar_vectores(vectores_docs, vector_consulta):
    """
    Muestra únicamente los primeros 5 elementos de cada embedding.
    """

    print("=" * 60)
    print("PRIMEROS 5 VALORES DE CADA VECTOR")
    print("=" * 60)

    for i, vector in enumerate(vectores_docs):
        primeros = [f"{valor:.4f}" for valor in vector[:5]]
        print(f"Documento {i + 1}: {primeros}")

    primeros = [f"{valor:.4f}" for valor in vector_consulta[0][:5]]

    print("\nConsulta:")
    print(primeros)


def calcular_similitudes(vectores_docs, vector_consulta):
    """
    Calcula la similitud del coseno entre la consulta
    y todos los documentos.
    """

    similitudes = cosine_similarity(vector_consulta, vectores_docs)

    return similitudes[0]


def mostrar_resultados(documentos, similitudes):
    """
    Ordena los documentos de mayor a menor similitud
    y muestra los resultados.
    """

    print("\n")
    print("=" * 60)
    print("RESULTADOS")
    print("=" * 60)

    indices = np.argsort(similitudes)[::-1]

    for posicion, indice in enumerate(indices, start=1):

        print(f"\n{posicion}. Documento {indice + 1}")
        print(f"Texto      : {documentos[indice]}")
        print(f"Similitud  : {similitudes[indice]:.4f}")


def mostrar_mejor_documento(documentos, similitudes):
    """
    Muestra el documento con mayor similitud.
    """

    indice = np.argmax(similitudes)

    print("\n")
    print("=" * 60)
    print("DOCUMENTO MÁS RELEVANTE")
    print("=" * 60)

    print(f"Documento : {indice + 1}")
    print(f"Texto     : {documentos[indice]}")
    print(f"Similitud : {similitudes[indice]:.4f}")

    print("\nConclusión:")

    print(
        f'El documento más similar a la consulta es el Documento {indice + 1}, '
        f'ya que obtuvo la mayor similitud del coseno '
        f'({similitudes[indice]:.4f}).'
    )


def main():

    documentos = [
        "pintura de monedas",
        "monedas de mundo",
        "25 centavos americanos",
        "billetes ecuatorianos",
    ]

    consulta = "colecciones de monedas"

    try:

        validar_entrada(documentos, consulta)

        modelo = cargar_modelo()

        vectores_docs, vector_consulta = generar_embeddings(
            modelo,
            documentos,
            consulta,
        )

        mostrar_vectores(
            vectores_docs,
            vector_consulta,
        )

        similitudes = calcular_similitudes(
            vectores_docs,
            vector_consulta,
        )

        mostrar_resultados(
            documentos,
            similitudes,
        )

        mostrar_mejor_documento(
            documentos,
            similitudes,
        )

    except Exception as error:
        print("\nOcurrió un error:")
        print(error)


if __name__ == "__main__":
    main()
```
