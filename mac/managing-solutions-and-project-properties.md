---
title: Administrar propiedades de soluciones y proyectos
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: fefb6c5e67b21907150611b3639cc16c05812e1a
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---
# <a name="managing-project-and-solution-properties"></a>Administrar propiedades de soluciones y proyectos

## <a name="project-options"></a>Opciones de proyecto 

Las opciones de proyecto son específicas de cada proyecto y afectan al modo en que este se escribe, se compila y se ejecuta. Esto contrasta con las preferencias de Visual Studio para Mac, que establecen opciones específicas del usuario, y con las opciones de solución, que establecen las opciones de toda la solución. Las opciones de proyecto se almacenan en el archivo de proyecto (.csproj), para que otros desarrolladores puedan compilar y ejecutar el proyecto correctamente. Esto permite que muchos programadores trabajen en el mismo documento sin poner en peligro el formato del archivo.

Las opciones de proyecto de Visual Studio para Mac se pueden iniciar al hacer doble clic en el nombre del proyecto o al hacer clic con el botón derecho para abrir el menú contextual y seleccionar **Opciones**:

 ![Opción del menú contextual](media/projects-and-solutions-image2.png)

Las opciones editables incluyen las usadas para compilar, ejecutar y establecer opciones de código fuente y control de versiones.

Las opciones de proyecto se organizan en cinco categorías diferentes que tienen las siguientes capacidades:

* **General**: aquí se puede establecer alguna información del proyecto, como Nombre, Descripción y Espacio de nombres predeterminado, junto con la ubicación del proyecto.
* **Compilar**: aquí los desarrolladores pueden establecer o cambiar perfiles de PCL de bibliotecas de clases portables. También se pueden establecer comandos personalizados, configuraciones y opciones del compilador. Aquí también se pueden establecer la ruta de acceso de la salida y el nombre del ensamblado.
* **Ejecutar**: permite crear configuraciones de ejecución personalizadas proyecto a proyecto.
* **Código fuente**: permite controlar el formato de muchos tipos de archivo diferentes y convenciones de nomenclatura. También se pueden establecer las directivas de nomenclatura y los estilos de encabezado predeterminados.
* **Control de versiones**: permite editar el estilo del mensaje de confirmación al usar el control de versiones con el proyecto.

Cada proyecto además puede contener opciones de proyecto concretas, según la plataforma. Por ejemplo, un proyecto de Xamarin.Android, como el que se muestra a continuación, tendrá opciones relacionadas con la compilación de Android (como las opciones del enlazador) y la aplicación (como los permisos):

 ![Opciones de proyecto de Android](media/projects-and-solutions-image5.png)

Xamarin.iOS contiene opciones relacionadas con la firma de lote, como el perfil de aprovisionamiento necesario que se va a usar, y relacionadas con las opciones de empaquetado de IPA:

 ![Opciones de proyecto de iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Opciones de solución 

Las opciones de solución son como las opciones de proyecto, aunque abarcan toda la solución. Proporcionan una manera de establecer la información del autor, la configuración de compilación, los estilos de formato de código y el control de versiones y una forma de asignar el proyecto de inicio de la solución.  Se puede acceder al cuadro de diálogo Opciones de la solución desde el elemento de menú **Proyecto > Opciones de la solución**, desde el elemento de menú contextual **Opciones** de la solución en el Panel de solución o al hacer doble clic en la solución en el Panel de solución:

 ![Opciones de solución](media/projects-and-solutions-image7.png)

