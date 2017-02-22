---
title: "Procedimientos recomendados para implementar un complemento de Control de c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de código fuente plug-ins, procedimientos recomendados"
  - "mejores prácticas, los complementos de control de código fuente"
  - "control de código fuente [Visual Studio SDK], complementos"
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedimientos recomendados para implementar un complemento de Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los detalles técnicos siguientes pueden ayudarle a implementar un complemento de control de código fuente de forma confiable [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Problemas de administración de memoria  
 En la mayoría de los casos, el entorno de desarrollo integrado \(IDE\), que es el autor de la llamada, se libera y asigna la memoria. El complemento de control de código fuente devuelve cadenas y otros elementos de búferes asignados al llamador. Las excepciones se indican en las descripciones de funciones específicas donde se producen.  
  
## Matrices de nombres de archivo  
 Cuando se pasa una matriz de archivos, no se pasa como una matriz contigua de nombres de archivo. Se pasa como una matriz de punteros a los nombres de archivo. Por ejemplo, en la [SccGet](../extensibility/sccget-function.md), los nombres de archivo se pasan por el `lpFileNames` parámetro, donde `lpFileNames` es un puntero a un `char **`.`lpFileNames`\[0\] es un puntero al nombre, `lpFileNames`\[1\] es un puntero para el nombre de la segunda y así sucesivamente.  
  
## Modelo de gran tamaño  
 Todos los punteros son de 32 bits, incluso en sistemas operativos de 16 bits.  
  
## Rutas de acceso completas  
 Donde los nombres de archivos o directorios se especifican como argumentos, deben ser rutas de acceso completas o rutas de acceso UNC, sin barras invertidas final. Es responsabilidad del complemento para traducir a rutas de acceso relativas si es un requisito del sistema de control de código fuente subyacente del control de origen.  
  
## Especifique una ruta de acceso completa para el archivo DLL registrado  
 El IDE ya no carga archivos DLL de rutas de acceso relativas \(por ejemplo,.\\NewProvider.dll\). Debe especificarse una ruta de acceso completa del archivo DLL \(por ejemplo, C:\\Providers\\NewProvider.dll\). Este requisito refuerza la seguridad del IDE evitando la carga de archivos DLL de control de origen no autorizados o suplantado.  
  
## Buscar un complemento de VSSCI existente al instalar el complemento de Control de código fuente  
 Un usuario que planea instalar el complemento de control de código fuente que ya tiene un origen control existente complemento instalado en el equipo. El programa de instalación del complemento que cree debe determinar si existen valores existentes para las claves del registro. Si ya se establecen estas claves, el programa de instalación debe preguntar al usuario si desea registrar el complemento como el complemento de control de código fuente predeterminado y reemplazar el que ya está instalado.  
  
## Códigos de resultado de error e informes  
 El `SCC_OK` devuelve el código de una función de control de origen indica que la operación se ha realizado correctamente para todos los archivos. Si se produce un error en la operación, se espera para devolver el último código de error encontrado.  
  
 La regla para los informes es que, si se produce un error en el IDE, el IDE es responsable de informar del mismo. Si se produce un error en el sistema de control de código fuente, el complemento de control de código fuente es responsable de informar de él. Por ejemplo, "no hay archivos seleccionados", se mostrarían por el IDE, mientras que "este archivo ya está desprotegido", se mostrarían por el complemento.  
  
## La estructura de contexto  
 Durante la llamada a la [SccInitialize](../extensibility/sccinitialize-function.md), las fases de llamador el `ppvContext` parámetro, que es un identificador sin inicializar a void. El complemento de control de código fuente puede pasar por alto este parámetro o se puede asignar una estructura de cualquier tipo y colocar un puntero a esa estructura en el puntero pasado. El IDE no entiende esta estructura, pero pasa un puntero a esta estructura en todas las llamadas en el complemento. Esto proporciona información de caché de contexto valiosos para el complemento que puede utilizar para mantener la información de estado global que se conserva en las llamadas de función sin el uso de variables globales. El complemento es responsable de liberar la estructura en una llamada a la [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Si el complemento establece el `SCC_CAP_REENTRANT` de bits en el [SccInitialize](../extensibility/sccinitialize-function.md) \(específicamente, en la `lpSccCaps` parámetro\), varias estructuras de contexto se utilizan para realizar un seguimiento de todos los proyectos que están abiertos.  
  
## Marcadores de bits y otras opciones del comando  
 Para cada comando, como el [SccGet](../extensibility/sccget-function.md), el IDE puede especificar muchas opciones que cambian el comportamiento del comando.  
  
 La API admite la configuración de determinadas opciones en el IDE mediante el `fOptions` parámetro. Estas opciones se describen en [Marcadores de bits que se utilizan los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) junto con los comandos que afectan a. En general, estas son opciones que el usuario no recibirá.  
  
 Más opciones de configuración configurables por el usuario no se definen de esta manera, porque varían enormemente entre los complementos de control de código fuente. Por lo tanto, el mecanismo recomendado es un **avanzadas** botón. Por ejemplo, en la **obtener** cuadro de diálogo, el IDE muestra sólo la información que comprende, pero también muestra un **avanzadas** botón si el complemento tiene opciones para este comando. Cuando el usuario hace clic en el **avanzadas** button, las llamadas IDE el [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) para habilitar el control de código fuente para pedir al usuario información acerca de los marcadores de bits o una fecha y hora. El complemento devuelve esta información en una estructura que se pasa de nuevo durante el `SccGet` comando.  
  
## Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [Creación de un Control de origen de complemento](../extensibility/internals/creating-a-source-control-plug-in.md)