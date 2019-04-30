---
title: Panel publicar, Diseñador de proyectos (desarrollo de Office en Visual Studio)
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 84a62fc796243172c9130c8113c4e6d289ed3092
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447017"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Panel publicar, Diseñador de proyectos (desarrollo de Office en Visual Studio)
  La página **Publicar** del **Diseñador de proyectos** se usa para configurar las propiedades de la implementación.

 Para acceder a esta página, seleccione el proyecto en el **Explorador de soluciones**y luego, en el menú **Proyecto** , elija *Propiedades de* **nombreDelProyecto**. Si no se muestra la página **Publicar** , elija la pestaña **Publicar** .

> [!NOTE]
> También puede establecer la ubicación de publicación en el **Asistente para publicación**. Para obtener más información, vea [Cómo: Publicar una solución de Office mediante ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).

## <a name="uielement-list"></a>Lista de UIElement
 **Ubicación (sitio web, servidor ftp o ruta de acceso de archivo) de la carpeta de publicación** necesarios.

 La ubicación de la carpeta de publicación es el directorio donde Visual Studio copia los archivos de la solución como, por ejemplo, los manifiestos, los ensamblados y otros archivos de la compilación. Es necesario tener acceso de escritura a este directorio.

 Las opciones incluyen el equipo local, un recurso compartido de archivos UNC o un sitio web HTTP/HTTPS. La ruta de acceso puede ser local (*c:\foldername\publishfolder*), relativo (*publicar\\*), o una ubicación completa (*\\\servername\foldername* o http://<em>nombreDeServidor/nombreDeCarpeta</em>).

 De forma predeterminada, la ubicación de publicación es *http://localhost/projectname/* si tiene IIS instalado, o el *publicar\\*  directorio si no tiene IIS instalado.

 **Dirección URL de la carpeta de instalación** opcional.

 La URL de la carpeta de instalación es el directorio desde el que el usuario final instalará la personalización. También es la ruta de acceso que usará la solución para buscar actualizaciones. La ruta de acceso puede ser igual que la ubicación de la carpeta de publicación, pero esto no es un requisito.

 Las opciones incluyen el equipo local, un recurso compartido de archivos UNC o un sitio web HTTP/HTTPS. La ruta de acceso puede ser local (*c:\foldername\publishfolder*), relativo (*publicar\\*), o una ubicación completa (*\\\servername\foldername* o http://<em>nombreDeServidor/nombreDeCarpeta</em>). Todas las ubicaciones HTTP/HTTPS se deben crear con caracteres US-ASCII. No se admiten caracteres Unicode.

 Si se establece la ruta de instalación, los archivos de personalización deben estar en dicha ubicación para que los usuarios instalen la personalización. La ubicación solo debe establecerse si conoce la ubicación de implementación final.

 Si los archivos de instalación están en una ubicación relativa al documento o al programa de instalación, como sucede con la opción de CD, deje este cuadro en blanco.

 Un administrador puede asignar este valor más adelante. Para obtener más información, vea [Cómo: Cambiar la ruta de instalación de una solución de Office](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).

 **Requisitos previos** los requisitos previos pueden incluirse con el programa de instalación o descarga a petición durante la instalación.

- **Descargar los requisitos previos del sitio web del proveedor de componentes**: Use esta opción para descargar los requisitos previos de Microsoft.

- **Descargar los requisitos previos desde la misma ubicación que mi aplicación**: Use esta opción para empaquetar los requisitos previos en el instalador. Si se incluyen los archivos de los requisitos previos con el programa de instalación, aumenta el tamaño de la solución.

- **Descargar requisitos previos de la siguiente ubicación**: Use esta opción para que los requisitos previos disponibles para los usuarios finales como cualquier otro programa de instalación en una página web o recurso compartido de red.

  **Las actualizaciones** el intervalo de actualización determina la frecuencia con la solución busca actualizaciones. El valor predeterminado es buscar cada siete días.

  Si se buscan actualizaciones cada vez que se carga una personalización de nivel de documento o un complemento de VSTO, se mantendría actualizada la instalación, pero afectaría al rendimiento de inicio.

  Si va a implementar mediante un CD o una unidad extraíble, establezca esta propiedad en **No buscar actualizaciones**.

  **Opciones (descripción)** se pueden establecer las opciones de publicación de las siguientes propiedades:

- Idioma de publicación: la configuración regional de la solución de Office.

- Nombre del publicador: el nombre de la compañía o el desarrollador tal y como aparece en **Agregar o quitar programas** o **Programas y características**.

- Nombre del producto: el nombre de la solución de Office tal como aparece en **Agregar o quitar programas** o **Programas y características**.

- Dirección URL de soporte: la ubicación para que los usuarios finales puedan ponerse en contacto con el servicio de soporte técnico de la solución de Office.

  **Opciones (configuración de Office)** se pueden establecer las opciones de publicación de las siguientes propiedades:

- Nombre de la solución: el nombre de la solución de Office tal como aparece en la aplicación de Office.

- Descripción: la descripción de la solución de Office tal como aparece en la aplicación de Office.

- Comportamiento de carga del complementos de VSTO:

  - Cargar al inicio: especifica que el complemento de VSTO se carga cuando se inicia la aplicación de Office.

  - Cargar a petición: especifica que el complemento de VSTO se carga cuando la aplicación lo requiere; por ejemplo, cuando un usuario hace clic en un elemento de la interfaz de usuario que usa funcionalidad del complemento de VSTO.

  **Idioma de publicación** esta opción establece el idioma de los términos de licencia del Software de Microsoft e incluye los paquetes de idioma en la lista de requisitos previos. No afecta al idioma de la personalización. Los idiomas instalados de Visual Studio determinan el idioma del programa de instalación.

  Para obtener más información sobre cómo cambiar la **idioma de publicación**, vea [Cómo: Cambiar el idioma de publicación para una aplicación ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md).

  **Publicar versión** establece el número de versión para la personalización. Cuando se cambia el número de versión, la aplicación se publica como una actualización. Durante el proceso de compilación se crea una nueva carpeta para cada versión, lo que evita que se sobrescriba la versión previamente publicada. Cada parte de la versión de publicación (**Principal**, **Secundaria**, **Compilación**, **Revisión**) puede contener hasta cinco dígitos.

  **Incrementar revisión automáticamente con cada versión** opcional. Si esta opción está seleccionada (valor predeterminado), la parte **Revisión** del número de versión se incrementa de a una unidad cada vez que se publica la personalización. Esto hace que la personalización se publique como una actualización.

  **Publicar ahora** publica la aplicación mediante la configuración actual. Equivalente al botón **Finalizar** del **Asistente para publicación**.

## <a name="see-also"></a>Vea también

- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
- [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Requisitos previos de la solución de Office para implementación](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e)
