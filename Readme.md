#PythonDeveloper
## introduccion completa a python - Cython - Frameworks - Inteligencia Artificial

# Python (3.8) a (3.12)  - Documento

## 1. Sobre Python

python es un lenguaje de programacion bastante robusto en la ahora aplicada inteligencia artificial y otras herramientas que desde la automatizacion es bastante agil desarrollar aspectos completos sin mucho dependencia de software
tambien que en este repositorio se almacenara gran parte de la introduccion compartida de los restos de python como lenguaje de programacion formalizada y otros aspectos tanto fundamentales para un solido arranque de este lenguaje
- el contenido tambien aplicara a sus derivantes en otras versiones como tambien a conda - (Cython) - (Jpython).
Parte de la introduccion sera corta para complementar la introduccion sobre el lenguaje de programacion Python - Fundamentos

## 2. Arquitectura General

La arquitectura de los archivos de base de este repositorio se iran actualizando a medida se desarrolle el contenido tratara de ser lo mas practico posible con el manejo de tags en el apartado de github de TagV0.1 
python tambien tiene aspectos importante que se aplicara a demostrar su desarrollo a niveles mas extendidos 

- **Librerias**: el lenguaje de base tiene a Pypi como gestor de paquetes adicionales a python, Pypywhere entre otras que tambien permiten realizar la instalacion de otras librerias 
- **dependencias**: Python tiene bastantes dependencias y soporte en la mayoria de las areas de desarrollo en IA, Desarrollo Web y otros 
- **Apis**: Compatible extensivamente con multiples herramientas web y tambien para gestionar herramientas actuales ya lo incorporan existen varias que son completamnte aplicables
- **Frameworks**: Contiene entre los mas populares para desarrollo web (Django - Flask).

Las carpetas existentes componen : 

```mermaid
graph python#-1
    subgraph Conociendo al Lenguaje
        C1[introduccion 1]
        C2[Path-Variables-Versiones 2]
        C3[Comandos-cli 3]
		C3[Lenguaje-Doc 4]
		C3[Recapitulacion 4]
    end

    subgraph Python#-2
        py-2[Variables-1]
		py-2[Tipos-Variables-1]
    end
	subgraph Python#-3
        S[python3]
    end
	subgraph Python#-4
        S[python4]
    end
	subgraph Python#-5
        S[python5]
    end
	subgraph Python#-6
        S[python6]
    end
	subgraph Python#-7
        S[python7]
    end
	subgraph Python#-8
        S[python8]
    end

	subgraph Python#-9
        S[python9]
    end
	subgraph Python#-10
        S[python10]
    end
	
	
   
    subgraph Componentes Comunes
        CC[Clases Comunes]
    end

   
```

## 3. Componentes Clave y sus Interacciones

### 3.1. Servicios con Python

El servidor es una aplicación Java que contiene las siguientes clases principales:

### 3.2. Clases - Avanzadas

El servidor es una aplicación Java que contiene las siguientes clases principales:

### 3.3. Polimofismo aplicado a los Hilos - Multihilo


## 4. Flujo de Operación

1.  **Inicio del Servidor**: El `ServerLauncher` se inicia y permite al usuario iniciar el `ChatServer` en el puerto 12345. El indicador de estado se vuelve verde cuando el servidor está activo.
2.  **Conexión del Cliente**: Un `ChatClient` se inicia. El usuario introduce un Nick y la dirección IP del servidor. El cliente intenta conectarse al servidor con un bucle de reintento en caso de fallo de conexión.
3.  **Gestión de Sesión**: Una vez conectado, el servidor crea un `ClientHandler` para el nuevo cliente. El cliente envía su Nick. El servidor genera una ID de sesión única (IP + Nick, acortada) y la registra. El servidor envía la clave AES al cliente y difunde la lista actualizada de usuarios a todos los clientes.
4.  **Cifrado de Comunicación**: Todos los mensajes de texto y datos de archivo se cifran utilizando AES antes de ser enviados a través de la red y se descifran al recibirlos. Cada sesión tiene su propia clave AES.
5.  **Envío de Mensajes**: Un cliente escribe un mensaje, lo cifra y lo envía al servidor como un objeto `Message`. El `ClientHandler` del servidor recibe el objeto `Message`, lo descifra, lo retransmite a todos los demás `ClientHandler`s, que a su vez lo cifran y lo envían a sus respectivos clientes. Los clientes descifran y muestran el mensaje. Los mensajes enviados por el propio usuario se muestran inmediatamente en la interfaz con un estilo distintivo.
6.  **Desencriptación a Demanda**: Los mensajes recibidos de otros usuarios se muestran inicialmente en su forma cifrada. Al hacer clic en un mensaje cifrado en el `chatPane`, el contenido se desencripta y se muestra en texto legible. Esto permite a los usuarios controlar cuándo y qué mensajes desean descifrar.
7.  **Envío de Archivos**: Un cliente selecciona un archivo (máx. 10MB), el `ChatClient` lo lee, lo cifra y lo envía al servidor como un objeto `FileMessage`. El servidor lo retransmite a los clientes, que lo descifran y lo guardan localmente. Se ha mejorado el manejo de errores y el cierre de recursos.
8.  **Gestión de Desconexión/Reconexión**: El cliente puede hacer clic en el botón "Desconectar" para cerrar su conexión. El servidor maneja esta desconexión, elimina al usuario de la lista de activos y difunde la lista actualizada. El cliente puede entonces intentar reconectarse a la sala de chat.

## 5. Servicios Web Python Frameworks



## 6. Sesiones usuario sistemas Nivel de Seguridad 0 - 1 
Se utiliza el algoritmo de cifrado simétrico AES (Advanced Encryption Standard) con claves de 128 bits. Cada `ClientHandler` genera su propia clave AES, que se envía al cliente al establecer la conexión. Esto asegura que la comunicación entre un cliente y el servidor esté cifrada de forma única.


La información de la sesión de usuario (Nick, ID de sesión, etc.) se gestiona en memoria en el servidor. La clase `UserSession` es `Serializable`, lo que permitiría en un futuro la persistencia de estos datos a un archivo si fuera necesario, sin depender de una base de datos externa.

## 7. Servicios Compartidos Python Sockets

El sistema permite el envío de archivos de hasta 10MB. Los archivos se envían como objetos `FileMessage` que contienen el nombre del archivo y los datos binarios cifrados. Se ha implementado la validación del tamaño del archivo en el cliente y el manejo de la recepción y guardado en el cliente.

## 8. Consideraciones de Seguridad

-   **Cifrado AES**: Asegura la confidencialidad de los datos en tránsito.
-   **Generación de ID de Sesión**: La ID se basa en IP y Nick para una identificación única, aunque no es un mecanismo de autenticación robusto. Para un entorno de producción, se requeriría un sistema de autenticación y autorización más sofisticado.
-   **Manejo de Errores**: Se ha mejorado el manejo de excepciones de red y de cifrado para hacer el software más robusto.

## 9. Pruebas Finales

Se han realizado las siguientes pruebas para verificar la funcionalidad del sistema:

-   **Visibilidad de Mensajes**: Se verificó que los mensajes de texto y archivos se retransmiten correctamente a todos los clientes, excluyendo al remitente. El formato `[nickname]: [mensaje]` se aplica consistentemente.
-   **Conexión de Clientes**: Se verificó que múltiples clientes pueden conectarse al servidor simultáneamente. El bucle de reintento en el cliente mejora la experiencia de conexión.
-   **Envío de Mensajes de Texto**: Se confirmó que los mensajes de texto se envían y reciben correctamente entre clientes a través del servidor, con cifrado y descifrado AES. Los mensajes propios se muestran en tiempo real y con el formato `[nickname]: [mensaje]`.
-   **Cifrado/Descifrado AES**: Se validó que los mensajes y los datos de los archivos se cifran antes de ser enviados y se descifran correctamente al ser recibidos. La funcionalidad de desencriptación a demanda ha sido probada y funciona correctamente.
-   **Gestión de Sesiones**: Se comprobó que el servidor gestiona las sesiones de los usuarios (Nick, IP, ID de sesión) de forma adecuada.
-   **Envío y Recepción de Archivos**: Se verificó el envío y recepción de archivos de hasta 10MB, incluyendo el cifrado y descifrado de los datos del archivo y el nombre del archivo. El límite de tamaño se aplica correctamente.
-   **Manejo de Desconexiones**: Se probó que la desconexión de un cliente es manejada correctamente por el servidor y que los recursos (sockets, streams) se cierran adecuadamente. La reconexión funciona como se espera.
-   **Lista de Usuarios Conectados**: Se verificó que la lista de usuarios conectados se actualiza en tiempo real en la interfaz del cliente cuando los usuarios se conectan o desconectan.
-   **Lanzador del Servidor**: Se probó que el `ServerLauncher` inicia y detiene el servidor correctamente, y que el indicador de estado refleja el estado actual del servidor.
-   **Mejoras de UI/UX**: Se ha verificado que la interfaz de usuario es más atractiva y funcional, con estilos de mensajes diferenciados y una barra de estado.

## 10. Guía de Sobre Python(3.8) a (3.12)

Esto compilará las clases del servidor y del cliente, colocando los archivos `.class` en sus respectivos directorios (`server/` y `client/`).

## 11. Inteligencia Artificial - Demox

-   **Persistencia de Sesiones**: Implementar la serialización de las sesiones de usuario a un archivo para que persistan entre reinicios del servidor.
-   **Manejo de Errores Mejorado**: Añadir un manejo de errores más robusto y mensajes de usuario más informativos.
-   **Chat Privado**: Implementar la funcionalidad de chat privado entre dos usuarios específicos.
-   **Notificaciones de Archivos**: Mejorar la notificación de archivos recibidos y la gestión de descargas.
-   **Seguridad Avanzada**: Explorar mecanismos de autenticación más robustos y gestión de claves AES más sofisticada.


