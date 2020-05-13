---
title: 'Zona de prueba 7: Compartir ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd4c48e94015d95f5e56d465cdbf98562108d3b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704405"
---
# <a name="test-area-7-share"></a>Área de prueba 7: compartir
Esta área de prueba cubre el uso compartido de elementos entre ubicaciones mediante el comando **Compartir.**

 Una operación hhare es la aparente duplicación de archivos y elementos de carpeta entre dos o más ubicaciones dentro de una jerarquía de archivos de control de código fuente. La duplicación no se produce realmente en el servidor, pero el usuario ve el mismo archivo en dos o más ubicaciones especificadas. Cada vez que se realizan cambios en cualquiera de los elementos compartidos, esos cambios aparecen en todas las demás ubicaciones compartidas.

 Compartir en carpetas funciona si selecciona una carpeta con al menos un archivo bajo control de código fuente en ella. El comando share está deshabilitado en las siguientes condiciones:

- Si la carpeta seleccionada es una carpeta vacía.

- Si hay una carpeta real, pero no contiene archivos de control de código fuente.

- Si hay una carpeta virtual, si los archivos bajo control de código fuente están en ella o no.

- Si hay un proyecto Web de sitio remoto.

## <a name="command-menu-access"></a>Acceso al menú de comandos
 Las [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siguientes rutas de menú del entorno de desarrollo integrado se utilizan en los casos de prueba.

 Compartir:**Compartir** **control**->**Source Control**->de código fuente de archivos .

## <a name="expected-behavior"></a>Comportamiento esperado

- El archivo compartido aparece en la ubicación compartida.

- Al ver el historial del almacén de versiones del control de código fuente, se muestra que los archivos se comparten.

- La edición de un archivo compartido edita ambas ubicaciones del archivo.

## <a name="test-cases"></a>Casos de prueba
 Los siguientes son casos de prueba específicos para el área de prueba Compartir.

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Compartir un archivo de un proyecto cargado bajo control de código fuente a otro proyecto cargado|1. Cree un nuevo proyecto.<br />2. Agregue un segundo proyecto a la solución.<br />3. Cree un archivo en el segundo proyecto con un nombre que no esté en el primer proyecto.<br />4. Agregue la solución al control de código fuente.<br />5. Seleccione el primer proyecto.<br />6. Abra el cuadro de diálogo **Compartir** (**Compartir** -> **control** -> **Share**de código fuente de archivos ).<br />7. Comparta el archivo del segundo proyecto al primer proyecto.<br />8. Acepte **desproteger** si se le solicita.|Comportamiento esperado común.|
|Compartir un archivo de un proyecto a otro|1. Cree un nuevo proyecto.<br />2. Añádalo al control de código fuente.<br />3. Cierre la solución.<br />4. Crear un segundo proyecto (nueva solución.)<br />5. Agregue la solución al control de código fuente.<br />6. Seleccione el proyecto.<br />7. Abra el cuadro de diálogo **Compartir** (**Compartir** -> control -> **Share**de**código fuente**de archivos ).<br />8. Comparta un archivo del proyecto agregado anteriormente al proyecto abierto.<br />9. Acepte **Desproteger** si se le solicita.|Comportamiento esperado común.|
|Compartir un archivo que no forma parte del proyecto desde el control de código fuente en el proyecto cargado actualmente|1. Cree un nuevo proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Agregue un archivo al control de código fuente que no forme parte del proyecto o la solución.<br />4. Seleccione el proyecto y abra el cuadro de diálogo **Compartir** **(** -> **Compartir****control** -> de código fuente de archivos ).<br />5. Seleccione un archivo dentro del cuadro de diálogo **Compartir** que no exista dentro del proyecto o solución actual y compártalo.<br />6. Acepte **Desproteger** si se le solicita.|El almacén de control de código fuente ha realizado un Get, por lo que el archivo está ahora en la ubicación local del proyecto.|
|Compartir archivos dentro del mismo proyecto a una carpeta diferente|1. Seleccione **Desproteger automáticamente** en Control de**código fuente**de**opciones** -> de **herramientas** -> .<br />2. Cree un nuevo proyecto y agréguelo al control de código fuente.<br />3. Agregue una carpeta al proyecto.<br />4. Agregue un archivo a la carpeta y compruebe la carpeta.<br />5. Seleccione la carpeta.<br />6. Abra el cuadro de diálogo **Compartir** (**Compartir** -> **control** -> **Share**de código fuente de archivos ).<br />7. Comparta el archivo en la carpeta seleccionada.|Comportamiento esperado común.<br /><br /> La carpeta debe protegerse con un archivo en ella antes de que se pueda usar para compartir.|
|Compartir una carpeta en el proyecto cargado — Recursivo|1. Cree un nuevo proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Seleccione el proyecto.<br />4. Abra el cuadro de diálogo **Compartir** (**Compartir** -> control -> **Share**de**código fuente**de archivos ).<br />5. Seleccione una carpeta.<br />6. Comparta la carpeta de forma recursiva en el proyecto.|Comportamiento esperado común.|
|Comparte varios archivos de un proyecto a otro|1. Cree un nuevo proyecto con varios archivos en él.<br />2. Agregue la solución al control de código fuente.<br />3. Cierre la solución.<br />4. Cree un nuevo proyecto en una nueva solución.<br />5. Agregue la solución al control de código fuente.<br />6. Seleccione el proyecto.<br />7. Abra el cuadro de diálogo **Compartir** (**Compartir** -> control -> **Share**de**código fuente**de archivos ).<br />8. Comparta varios archivos del proyecto creado anteriormente con el proyecto actualmente abierto.|Comportamiento esperado común.|

## <a name="see-also"></a>Vea también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
