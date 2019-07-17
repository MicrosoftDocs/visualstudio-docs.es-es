---
title: Registro de cambios (Visual Studio Tools para Unity, Mac) | Microsoft Docs
ms.custom: ''
ms.date: 04/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: e5bc02948d410d465d7ac1be798ff17ebc5daaf9
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821512"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Registro de cambios (Visual Studio Tools para Unity, Mac)

Registro de cambios de Visual Studio Tools para Unity.

## <a name="2020"></a>2.0.2.0

Publicada el 2 de abril de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con la actualización automática de la base de datos de recursos de Unity al guardarla. Esta característica está habilitada de forma predeterminada y desencadenará una recompilación en el lado de Unity al guardar un script en Visual Studio. Puede deshabilitar esta característica en la base de datos de recursos ubicada en Tools\Options\Tools for Unity\Refresh al guardarla.

  - Se ha agregado compatibilidad para configurar la instalación de Unity preferida para la documentación sin conexión.

  - Se ha agregado un menú contextual para el nuevo editor.

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - Se han corregido el filtrado de ensamblados y la inspección de marcos con marcos vacíos.

## <a name="2011"></a>2.0.1.1
 Publicada el 26 de marzo de 2019

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Convertir Mono temporalmente en la opción predeterminada y solo usar el depurador para esta versión tan específica.

## <a name="2006"></a>2.0.0.6

Publicada el 26 de marzo de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con "Asociar a Unity y reproducir".

## <a name="2005"></a>2.0.0.5

Publicada el 20 de marzo de 2019

### <a name="new-features"></a>Características nuevas

- **Generación de proyectos:**

  - Conservar las propiedades externas al procesar el archivo de solución.

## <a name="2004"></a>2.0.0.4

Publicada el 5 de marzo de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se actualizado la API ScriptableObject.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se han quitado los espacios de nombres de las plantillas.

## <a name="2003"></a>2.0.0.3
 Publicada el 5 de marzo de 2019

### <a name="new-features"></a>Características nuevas

- **Generación de proyectos:**

  - Los campos públicos y serializados ya no generarán advertencias. Hemos suprimido automáticamente las advertencias del compilador CS0649 y IDE0051 en los proyectos de Unity que crearon estos mensajes.

- **Integración:**

  - Solicitud de conexión a una instancia específica si hay más de un proceso de Unity en ejecución.

- **Evaluación:**

  - Se ha agregado compatibilidad con las funciones locales.

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - Se ha corregido la lectura de atributos personalizados de los argumentos con nombre al usar versiones de protocolo anteriores.

## <a name="2002"></a>2.0.0.2

Publicada el 4 de febrero de 2019

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha actualizado la API MonoBehaviour.

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - Se ha corregido la configuración de los valores primitivos en el depurador.

## <a name="2001"></a>2.0.0.1

Publicada el 4 de diciembre de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la contención automática del paquete de instalación.

## <a name="2000"></a>2.0.0.0
 Publicada el 4 de diciembre de 2018

### <a name="new-features"></a>Características nuevas

- **Depurador:**

  - Se ha reemplazado el depurador de Unity de Mac por el mismo depurador de Unity básico de Windows.

  - Se ha reemplazado NRefactory a favor de Roslyn para la evaluación de expresiones.

  - Se ha agregado compatibilidad con los punteros: desreferencia, conversión y aritmética de puntero (tanto Unity 2018.2+ y el nuevo tiempo de ejecución son necesarios para esto).

  - Se ha agregado compatibilidad con la vista del puntero de matrices (como en C++). Adopte una expresión de puntero y, a continuación, anexe una coma y el número de elementos que desea ver.

  - Se ha agregado compatibilidad con las construcciones asincrónicas.

  - Se ha agregado compatibilidad con las pseudovariables (identificadores de excepción y objetos).

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - Se ha corregido la evaluación de expresiones con expresiones con un formato incorrecto o no admitidas.

## <a name="1700"></a>1.7.0.0

Publicado el 13 de noviembre de 2018

### <a name="new-features"></a>Características nuevas

- **Depurador:**

  - Se ha agregado más información del cliente (IP, nombre del equipo) en el cuadro de diálogo Adjuntar.

### <a name="bug-fixes"></a>Correcciones de errores

- **Depurador:**

  - Se ha corregido un interbloqueo en la biblioteca usada para comunicarse con el motor de depuración de Unity, que hacía que Visual Studio o Unity se congelara, especialmente al ejecutar 'Asociar a Unity' o reiniciar el juego.

- **Integración:**

  - Se ha corregido la activación de los complementos de Unity cuando se seleccionaba otro editor predeterminado.

  - Se ha corregido la creación de plantillas de archivo de Unity.

## <a name="1602"></a>1.6.0.2

Publicado el 24 de julio de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se revirtió la solución a un error de rendimiento de Unity que se ha corregido en Unity.

## <a name="1601"></a>1.6.0.1

Publicado el 10 de julio de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Corrección de la compatibilidad con la coloración del sombreador.

## <a name="1600"></a>1.6.0.0

Publicado el 26 de junio de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Asistentes:**

  - Corrección de un error ortográfico en el mensaje OnApplicationFocus.

- **Generación de proyectos:**

  - Solución alternativa temporal de un error de rendimiento de Unity: MonoIslands en caché al generar proyectos.

  - No convierta más archivos PDB portátiles a MDB con el nuevo entorno de ejecución de Unity.

## <a name="1502"></a>1.5.0.2

Publicado el 18 de abril de 2018

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado la compatibilidad con la finalización del código básico del sombreador.

  - Se ha agregado la compatibilidad con la alternancia de comentarios en los archivos del sombreador.

## <a name="1501"></a>1.5.0.1

Publicado el 28 de marzo de 2018

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con las plantillas adicionales en el Explorador de proyectos de Unity.

## <a name="1500"></a>1.5.0.0

Publicado el 21 de marzo de 2018

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con la detección y conexión de reproductores Android conectados a través de USB.

## <a name="1403"></a>1.4.0.3

Publicado el 5 de marzo de 2018

### <a name="new-features"></a>Características nuevas

- **Generación de proyectos:**

  - Se ha agregado compatibilidad con el nuevo generador de proyectos en Unity 2018.1.

- **Integración:**

  - Se ha agregado un panel de opciones para la configuración dedicada.

## <a name="1402"></a>1.4.0.2

Publicado el 24 de enero de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Generación de proyectos:**

  - Se ha corregido la detección de la versión de Mono.

- **Integración:**

  - Se han corregido problemas de temporización con 2018.1 y la activación de complementos.

  - Se han corregido las notificaciones cuando se detecta un nuevo reproductor.

## <a name="1401"></a>1.4.0.1

Publicado el 23 de enero de 2018

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la expansión o contracción de carpetas al hacer doble clic.

## <a name="1400"></a>1.4.0.0

Publicado el 13 de diciembre de 2017

### <a name="new-features"></a>Características nuevas

- **Generación de proyectos:**

  - Se ha agregado compatibilidad con .NET Standard.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se corrigió la conversión del símbolo de depuración de pdb automático a mdb.

## <a name="1301"></a>1.3.0.1

Publicado el 12 de diciembre de 2017

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido la llamada indirecta a EditorPrefs.GetBool que afecta al inspector al tratar de cambiar el tamaño de la matriz.

- **Asistentes:**

  - Actualice el contexto de Roslyn antes de insertar el método.

## <a name="1300"></a>1.3.0.0

Publicado el 20 de noviembre de 2017

### <a name="new-features"></a>Características nuevas

- **Asistentes:**

  - Se ha agregado el asistente "Implementar mensaje de Unity".

  - Se ha agregado compatibilidad con la nueva API de finalización en VS para Mac 7.4.

## <a name="1200"></a>1.2.0.0

Publicado el 23 de octubre de 2017

### <a name="new-features"></a>Características nuevas

- **Depurador:**

  - Se ha agregado compatibilidad con archivos de símbolo de depuración portátiles.

### <a name="bug-fixes"></a>Correcciones de errores

- **Generación de proyectos:**

  - Se ha corregido un problema por el que la extensión .dll se agregaba erróneamente al nombre de archivo de ensamblado.

  - No fuerce el uso de la marca AllowAttachedDebuggingOfEditor de Unity, ya que el valor predeterminado es ahora "true".

## <a name="1103"></a>1.1.0.3

Publicado el 23 de octubre de 2017

### <a name="new-features"></a>Características nuevas

- **Generación de proyectos:**

  - Se ha agregado compatibilidad con el perfil de .NET 4.6.

## <a name="1102"></a>1.1.0.2

Publicado el 8 de agosto de 2017

### <a name="new-features"></a>Características nuevas

- **Depurador:**

  - Se inicia el cuadro de diálogo Asociar al proceso si no se está seguro de a qué Unity se asocia.

- **Generación de proyectos:**

  - Habilite siempre el modificador de compilación no seguro cuando se use Unity 5.6.

## <a name="1101"></a>1.1.0.1

Publicado el 20 de julio de 2017

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con los recursos localizados.

## <a name="1100"></a>1.1.0.0

Publicado el 12 de julio de 2017

### <a name="new-features"></a>Características nuevas

- **Integración:**

  - Se ha agregado compatibilidad con la asociación a reproductores y editores a través de la ventana Asociar al proceso.

- **Generación de proyectos:**

  - Se corrigieron las referencias al nombre de ensamblado con archivos mcs.rsp.

  - Se agregó compatibilidad con las unidades de compilación assembly.json.

  - Se corrigieron las definiciones con niveles de API.

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido un mensaje de error del sombreador al compilar.

## <a name="1001"></a>1.0.0.1

Publicado el 4 de mayo de 2017

### <a name="bug-fixes"></a>Correcciones de errores

- **Integración:**

  - Se ha corregido el seguimiento del documento activo con proyectos híbridos y normales.

## <a name="1000"></a>1.0.0.0

Publicado el 3 de mayo de 2017
