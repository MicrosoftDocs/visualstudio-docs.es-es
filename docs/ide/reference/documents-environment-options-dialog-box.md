---
title: "Documentos, Entorno, Opciones (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Environment.Documents"
  - "VS.ToolsOptionsPages.Environment.Documents"
  - "VS.ToolsOptionsPag.Environment.Documents"
helpviewer_keywords: 
  - "Documentos, Entorno, Opciones (cuadro de diálogo)"
  - "valores predeterminados, directorios"
  - "mensajes de error, personalizar"
  - "archivos [Visual Studio], opciones predeterminadas"
  - "archivos [Visual Basic], carga automática modificada"
  - "ventanas, personalizar el entorno"
  - "edición en memoria"
  - "carpetas [Visual Studio], especificar a dónde va el archivo abierto"
  - "Abrir archivo (cuadro de diálogo)"
  - "ventanas, habilitar la reutilización de la actual"
  - "notificaciones, archivos modificados"
  - "archivos [Visual Studio], mostrar en el Explorador de soluciones"
  - "directorios predeterminados"
  - "archivos de solo lectura, editar"
  - "Cuadro de diálogo Opciones, mostrar Archivos varios"
  - "directorios [Visual Studio], opciones del entorno de IDE"
  - "Cuadro de diálogo Opciones, página Documentos"
  - "advertencias, archivos modificados"
  - "Explorador de soluciones, mostrar archivos en"
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Documentos, Entorno, Opciones (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Use esta página del cuadro de diálogo **Opciones** para controlar la presentación de documentos en el entorno de desarrollo integrado \(IDE\) y administrar los cambios externos en los documentos y archivos.  Puede tener acceso a este cuadro de diálogo si selecciona **Opciones** en el menú **Herramientas** y elige **Documentos** en el nodo **Entorno**.  Si la página **Documentos** no aparece en la lista, seleccione **Mostrar todas las configuraciones** en el cuadro de diálogo **Opciones**.  
  
> [!NOTE]
>  Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Reutilizar la ventana de documento activa si se guardó**  
 Al seleccionar esta opción, se cierra el documento actual, en caso de que se haya guardado, y se abre un nuevo documento en la misma ventana.  Si no se ha guardado el documento actual, permanecerá abierto y el nuevo documento se abrirá en una ventana distinta.  Cuando esta opción está desactivada, los nuevos documentos siempre se abren en ventanas diferentes.  
  
 Pruebe esta opción si no realiza con frecuencia operaciones de cortar y pegar en varios documentos y desea minimizar el número de documentos y ventanas abiertos en su espacio de trabajo.  
  
 **Detectar si se modifica el archivo fuera del entorno**  
 Cuando se selecciona esta opción, aparece inmediatamente un mensaje que le informa de los cambios realizados en un archivo abierto por un editor fuera del IDE.  El mensaje le permite recargar el archivo desde su ubicación de almacenamiento.  
  
 **Cargar cambios automáticamente, si están guardados**  
 Una vez seleccionado **Detectar si se modifica el archivo fuera del entorno** y cuando un archivo abierto en el IDE cambie fuera del IDE, se generará un mensaje de advertencia de forma predeterminada.  Si se habilita esta opción, no aparece ninguna advertencia y el documento se vuelve a cargar en el IDE para tomar los cambios externos.  
  
 **Permitir la edición de archivos de sólo lectura; advertir al guardarlos**  
 Cuando esta opción está habilitada, puede abrir y editar un archivo de sólo lectura.  Cuando haya terminado, debe utilizar el  **Guardar como**comando para guardar el archivo con un nuevo nombre si desea guardar un registro de los cambios.  
  
 **Abrir archivo utilizando el directorio del documento activo actualmente**  
 Cuando está seleccionada, esta opción especifica que el cuadro de diálogo **Abrir archivo** mostrará el directorio del documento activo.  Cuando esta opción está desactivada, el cuadro de diálogo **Abrir archivo** muestra el último directorio utilizado para abrir un archivo.  
  
 **Comprobar que el fin de línea sea coherente al cargar**  
 Seleccione esta opción para que el editor examine los fines de línea de un archivo y muestre un cuadro de mensaje si se detectan incoherencias en el formato de los fines de línea.  
  
 **Mostrar advertencia si la operación Deshacer global modifica archivos editados**  
 Seleccione esta opción para mostrar un cuadro de mensaje cuando el comando **Deshacer global** deshaga los cambios de refactorización realizados en archivos que también se cambiaron después de la operación de refactorización.  Al devolver un archivo a su estado de previo a la refactorización, se podrían descartar los cambios posteriores realizados en el archivo.  
  
 **Mostrar archivos varios en el Explorador de soluciones**  
 Seleccione esta opción para mostrar el nodo **Archivos varios** en el **Explorador de soluciones**.  Los Archivos varios son archivos que no están asociados con un proyecto o a una solución, pero aparecen en el **Explorador de soluciones** por comodidad.  
  
> [!NOTE]
>  Seleccione esta opción para habilitar el comando **Ver en el explorador** del menú **Archivo** con el fin de mostrar los documentos Web no incluidos en la aplicación Web activa.  
  
 **\<** *n* **\> elementos guardados en el proyecto de archivos varios**  
 Especifica el número de archivos que se van a conservar en la carpeta **Archivos varios** del **Explorador de soluciones**.  Se muestran estos archivos aun cuando ya no estén abiertos en un editor.  Puede especificar cualquier número entero de 0 a 256.  El número predeterminado es 0.  
  
 Por ejemplo, si establece el valor de esta opción en 5 y hay 10 archivos varios abiertos, al cerrar esos 10 archivos, se seguirán mostrando los 5 primeros en la carpeta **Archivos varios**.  
  
 **Guardar documentos como Unicode cuando no se puedan guardar los datos en la página de códigos**  
 Seleccione esta opción para guardar como Unicode de manera predeterminada los archivos que contienen información incompatible con la página de códigos seleccionada.  
  
## Vea también  
 [Opciones de entorno \(Cuadro de diálogo\)](../../ide/reference/environment-options-dialog-box.md)   
 [Archivos varios](../../ide/reference/miscellaneous-files.md)   
 [Buscar y reemplazar texto](../../ide/finding-and-replacing-text.md)