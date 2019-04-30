---
title: 'Área de prueba 7: Recurso compartido de | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c0792871835d8adea52c1e4adfdfd2c38f7d617
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62857785"
---
# <a name="test-area-7-share"></a>Área de prueba 7: Compartir
Esta área de prueba trata para compartir elementos entre las ubicaciones a través de la **Share** comando.

 Una operación hhare es la duplicación aparente de archivos y carpetas de elementos entre dos o más ubicaciones dentro de una jerarquía de archivos de control de código fuente. Duplicación no produzca realmente en el servidor, pero el usuario vea el mismo archivo en dos o más ubicaciones especificadas. Cada vez que se realizan cambios en cualquiera de los elementos compartidos, esos cambios aparecerán en todas las demás ubicaciones compartidas.

 Uso compartido de carpetas funciona si selecciona una carpeta con al menos un archivo bajo control de código fuente en ella. El comando compartir está deshabilitado en las siguientes condiciones:

- Si la carpeta seleccionada es una carpeta vacía.

- Si hay una carpeta real, pero no contiene ningún archivo de control de código fuente.

- Si hay una carpeta virtual, si los archivos bajo control de código fuente están en él o no.

- Si hay un proyecto Web de sitio remoto.

## <a name="command-menu-access"></a>Acceso al menú de comandos
 La siguiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rutas de menú del entorno de desarrollo integrado que se usan en los casos de prueba.

 Compartir: **Archivo**->**Control de código fuente**->**Share**.

## <a name="expected-behavior"></a>Comportamiento esperado

- Archivo compartido aparece en la ubicación compartida.

- Ver el código fuente control versión almacén historial muestra que se comparten los archivos.

- Editar un archivo compartido edita las ubicaciones del archivo.

## <a name="test-cases"></a>Casos de prueba
 Los siguientes son casos de prueba concretos para el área de prueba de recurso compartido.

|Acción|Pasos de prueba|Resultados esperados para comprobar|
|------------|----------------|--------------------------------|
|Compartir un archivo de un proyecto cargado en el control de código fuente a otro proyecto cargado|1.  Cree un nuevo proyecto.<br />2.  Agregar un segundo proyecto a la solución.<br />3.  Cree un archivo en el segundo proyecto con un nombre que no está en el primer proyecto.<br />4.  Agregue la solución al control de código fuente.<br />5.  Seleccione el primer proyecto.<br />6.  Abra **Share** cuadro de diálogo (**archivo** -> **Control de código fuente** -> **recurso compartido**).<br />7.  Comparta el archivo desde el segundo proyecto al primer proyecto.<br />8.  Aceptar **desproteger** si se le solicita.|Comportamiento esperado común.|
|Compartir un archivo de un proyecto a otro|1.  Cree un nuevo proyecto.<br />2.  Agréguelo al control de código fuente.<br />3.  Cierre la solución.<br />4.  Cree un segundo proyecto (nueva solución).<br />5.  Agregue la solución al control de código fuente.<br />6.  Seleccione el proyecto.<br />7.  Abra el **recurso compartido** cuadro de diálogo (**archivo** -> **Control de código fuente** -> **compartir**).<br />8.  Compartir un archivo desde el proyecto agregado previamente al proyecto abierto.<br />9. Aceptar **desproteger** si se le solicita.|Comportamiento esperado común.|
|Compartir un archivo no forma parte del proyecto de control de código fuente en el proyecto cargado actualmente|1.  Cree un nuevo proyecto.<br />2.  Agregue la solución al control de código fuente.<br />3.  Agregar un archivo de control de código fuente que no forma parte de la solución o proyecto.<br />4.  Seleccione el proyecto y abra el **Share** cuadro de diálogo (**archivo** -> **Control de código fuente** -> **compartir**).<br />5.  Seleccione un archivo dentro de la **compartir** cuadro de diálogo que no existe en el proyecto actual o la solución y compartirlo.<br />6.  Aceptar **desproteger** si se le solicita.|El almacén de control de código fuente que haya realizado una operación Get, por lo que el archivo está ahora en la ubicación local del proyecto.|
|Compartir archivos dentro del mismo proyecto a una carpeta diferente|1.  Seleccione **desproteger automáticamente** en **herramientas** -> **opciones** -> **Control de código fuente**.<br />2.  Cree un nuevo proyecto y agregarlo al control de código fuente.<br />3.  Agregue una carpeta al proyecto.<br />4.  Agregue un archivo a la carpeta y compruebe en la carpeta.<br />5.  Seleccione la carpeta.<br />6.  Abra **Share** cuadro de diálogo (**archivo** -> **Control de código fuente** -> **recurso compartido**).<br />7.  Compartir archivos en la carpeta seleccionada.|Comportamiento esperado común.<br /><br /> Carpeta debe comprobarse con un archivo en él antes de que se puede usar para el recurso compartido.|
|Compartir una carpeta en el proyecto cargado, recursivos|1.  Cree un nuevo proyecto.<br />2.  Agregue la solución al control de código fuente.<br />3.  Seleccione el proyecto.<br />4.  Abra el **recurso compartido** cuadro de diálogo (**archivo** -> **Control de código fuente** -> **compartir**).<br />5.  Seleccione una carpeta.<br />6.  Compartir la carpeta de forma recursiva en el proyecto.|Comportamiento esperado común.|
|Compartir varios archivos de un proyecto a otro|1.  Cree un nuevo proyecto con varios archivos en ella.<br />2.  Agregue la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  Cree un nuevo proyecto en una nueva solución.<br />5.  Agregue la solución al control de código fuente.<br />6.  Seleccione el proyecto.<br />7.  Abra el **recurso compartido** cuadro de diálogo (**archivo** -> **Control de código fuente** -> **compartir**).<br />8.  Compartir varios archivos del proyecto creado anteriormente para el proyecto abierto.|Comportamiento esperado común.|

## <a name="see-also"></a>Vea también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)