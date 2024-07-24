Proyecto de Streamlit: Aplicación de Demostración
Esta es una aplicación de demostración creada con Streamlit que permite a los usuarios cargar archivos CSV para visualizar datos y crear gráficos interactivos.

Descripción del Proyecto
La aplicación consta de tres páginas principales:

Página Principal: Una página de bienvenida con instrucciones sobre cómo navegar por la aplicación.
Visualización de Datos: Una página donde los usuarios pueden cargar un archivo CSV y visualizar los datos, así como ver estadísticas descriptivas.
Gráficos Interactivos: Una página donde los usuarios pueden cargar un archivo CSV y crear gráficos interactivos seleccionando las columnas para los ejes X e Y.
Requisitos
Para ejecutar esta aplicación, necesitas tener instalados los siguientes paquetes de Python:

Streamlit
Pandas
Plotly
Puedes instalar estos paquetes usando pip:

bash
Copiar código
pip install streamlit pandas plotly
Estructura del Código
python
Copiar código
import streamlit as st
import pandas as pd
import plotly.express as px

def pagina_principal():
    st.title("Pagina Principal")
    st.write("Bienvenido a la aplicacion de demostracion")
    st.write("Usa el menu de la izquierda para navegar entre las paginas")
    
def visualizar_datos():
    st.title("Visualización de datos")
    st.write("Cargue un archivo CSV para visualizar datos")
    archivo_cargado = st.file_uploader("Elige un archivo CSV", type="csv")
    
    if archivo_cargado is not None:
        df = pd.read_csv(archivo_cargado)
        st.write("Datos del archivo CSV:")
        st.write(df)
        st.write("Estadisticas descriptivas:")
        st.write(df.describe())

def gráficos_interactivos():
    st.title("Gráficos interactivos")
    st.write("Carga un archivo CSV para crear gráficos interactivos")
    archivo_cargado = st.file_uploader("Elige un archivo CSV", type="CSV", key="2")
    
    if archivo_cargado is not None:
        df = pd.read_csv(archivo_cargado)
        st.write("Elige una columna para el eje X:")
        eje_x = st.selectbox("Eje X", df.columns)
        st.write("Elige una columna para el eje Y:")
        eje_y = st.selectbox("Eje Y", df.columns)
        
        if st.button("Crear Gráfico"):
            fig = px.bar(df, x=eje_x, y=eje_y, title=f"{eje_y} por {eje_x}")
            st.plotly_chart(fig)
    
st.sidebar.title("Navegacion")
pagina= st.sidebar.selectbox("Selecciona una pagina" , ["Página Principal", "Visualización de datos", "Gráficos interactivos"])

if pagina == "Página Principal":
    pagina_principal()
    
elif pagina == "Visualización de datos":
    visualizar_datos()
    
elif pagina == "Gráficos interactivos":
    gráficos_interactivos()
Instrucciones para Ejecutar la Aplicación
Clona este repositorio en tu máquina local.
Navega al directorio del proyecto.
Ejecuta el siguiente comando para iniciar la aplicación de Streamlit:
bash
Copiar código
streamlit run nombre_del_archivo.py
Abre tu navegador web y ve a http://localhost:8501 para ver la aplicación en funcionamiento.
Funcionalidades
Página Principal: Proporciona una breve introducción y guía de navegación.
Visualización de Datos: Permite cargar y visualizar datos de archivos CSV, junto con estadísticas descriptivas.
Gráficos Interactivos: Permite crear gráficos interactivos seleccionando columnas específicas del archivo CSV cargado.
