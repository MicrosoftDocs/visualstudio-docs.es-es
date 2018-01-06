---
title: 'Zona de ensayo 7: Compartir de | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f87ff08ea8d5e325ac66d923300927b59ab06452
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="test-area-7-share"></a>Probar el área 7: recurso compartido
Esta área de ensayo trata para compartir elementos entre las ubicaciones a través de la **recurso compartido** comando.  
  
 Una operación de hhare es la duplicación aparente de archivos y elementos de la carpeta entre dos o más ubicaciones dentro de una jerarquía de archivos de control de código fuente. Duplicación no se produce realmente en el servidor, pero el usuario vea el mismo archivo en dos o más ubicaciones especificadas. Cada vez que se realizan cambios en cualquiera de los elementos compartidos, esos cambios aparecerán en todas las demás ubicaciones compartidos.  
  
 Uso compartido en carpetas funciona si se selecciona una carpeta con al menos un archivo bajo control de código fuente en ella. El comando de recurso compartido está deshabilitado en las siguientes condiciones:  
  
-   Si la carpeta seleccionada es una carpeta vacía.  
  
-   Si hay una carpeta real, pero no contiene archivos de control de origen.  
  
-   Si no hay una carpeta virtual, si no hay archivos bajo control de código fuente en ella o no.  
  
-   Si hay un proyecto Web de sitio remoto.  
  
## <a name="command-menu-access"></a>Acceso al menú de comandos  
 El siguiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las rutas de acceso del menú de entorno de desarrollo integrado se utilizan en los casos de prueba.  
  
 Recurso compartido: **archivo**->**Control de código fuente**->**recurso compartido**.  
  
## <a name="expected-behavior"></a>Comportamiento esperado  
  
-   Archivo compartido aparece en la ubicación compartida.  
  
-   Ver origen control versión almacén historial se muestra en el que se comparten los archivos.  
  
-   Editar un archivo compartido edita las ubicaciones del archivo.  
  
## <a name="test-cases"></a>Casos de prueba  
 Éstos son los casos de prueba concretos para la zona de ensayo de recurso compartido.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Compartir un archivo desde un proyecto cargado bajo control de código fuente a otro proyecto cargado|1.  Cree un nuevo proyecto.<br />2.  Agregar un segundo proyecto a la solución.<br />3.  Crear un archivo en el segundo proyecto con un nombre que no está en el primer proyecto.<br />4.  Agregar la solución al control de código fuente.<br />5.  Seleccione el primer proyecto.<br />6.  Abra **recurso compartido** cuadro de diálogo (**archivo** -> **Control de código fuente** -> **recurso compartido**).<br />7.  Compartir el archivo desde el segundo proyecto al primer proyecto.<br />8.  Aceptar **desproteger** si se le solicita.|Comportamiento esperado común.|  
|Compartir un archivo de un proyecto a otro|1.  Cree un nuevo proyecto.<br />2.  Agregarlo al control de código fuente.<br />3.  Cierre la solución.<br />4.  Cree un segundo proyecto (solución de nuevo.)<br />5.  Agregar la solución al control de código fuente.<br />6.  Seleccione el proyecto.<br />7.  Abra la **recurso compartido** cuadro de diálogo (**archivo** -> **Control de código fuente** -> **recurso compartido**).<br />8.  Compartir un archivo desde el proyecto agregado previamente al proyecto abierto.<br />9. Aceptar **desproteger** si se le solicita.|Comportamiento esperado común.|  
|Compartir un archivo no forma parte del proyecto de control de código fuente en el proyecto cargado actualmente|1.  Cree un nuevo proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Agregue un archivo al control de código fuente que no forma parte de la solución o proyecto.<br />4.  Seleccione el proyecto y abra el **recurso compartido** cuadro de diálogo (**archivo** -> **Control de código fuente** -> **recurso compartido**).<br />5.  Seleccione un archivo dentro de la **compartir** cuadro de diálogo que no existen en el proyecto actual o la solución y compartirlo.<br />6.  Aceptar **desproteger** si se le solicita.|El almacén de control de código fuente realiza una operación Get, por lo que el archivo se encuentra ahora en la ubicación local del proyecto.|  
|Compartir archivos dentro del mismo proyecto a una carpeta diferente|1.  Seleccione **desproteger automáticamente** en **herramientas** -> **opciones** -> **Control de código fuente**.<br />2.  Cree un nuevo proyecto y agregarlo al control de código fuente.<br />3.  Agregar una carpeta al proyecto.<br />4.  Agregar un archivo a la carpeta y compruebe en la carpeta.<br />5.  Seleccione la carpeta.<br />6.  Abra **recurso compartido** cuadro de diálogo (**archivo** -> **Control de código fuente** -> **recurso compartido**).<br />7.  Recurso compartido de archivos en la carpeta seleccionada.|Comportamiento esperado común.<br /><br /> Carpeta debe comprobarse con un archivo en ella antes de que se puede utilizar para el recurso compartido.|  
|Compartir una carpeta en el proyecto cargado, recursivos|1.  Cree un nuevo proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Seleccione el proyecto.<br />4.  Abra la **recurso compartido** cuadro de diálogo (**archivo** -> **Control de código fuente** -> **recurso compartido**).<br />5.  Seleccione una carpeta.<br />6.  Compartir la carpeta de forma recursiva en el proyecto.|Comportamiento esperado común.|  
|Compartir varios archivos de un proyecto a otro|1.  Cree un nuevo proyecto con varios archivos en ella.<br />2.  Agregar la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  Cree un nuevo proyecto en una nueva solución.<br />5.  Agregar la solución al control de código fuente.<br />6.  Seleccione el proyecto.<br />7.  Abra la **recurso compartido** cuadro de diálogo (**archivo** -> **Control de código fuente** -> **recurso compartido**).<br />8.  Compartir varios archivos desde el proyecto creado anteriormente para el proyecto abierto actualmente.|Comportamiento esperado común.|  
  
## <a name="see-also"></a>Vea también  
 [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)