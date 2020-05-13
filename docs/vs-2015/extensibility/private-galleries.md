---
title: Galerías privadas ? Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 895fbef5459de75c7ccdc6a090fc30ec27a030f9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444926"
---
# <a name="private-galleries"></a>Private Galleries
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede compartir los controles, plantillas y herramientas que desarrolla publicándolos en una *galería privada* en la intranet de su organización, como se indica a continuación:  
  
- Cree una fuente Atom (RSS) en una ubicación central (repositorio) configurada adecuadamente en la intranet. Para obtener más información, consulte Cómo: crear una fuente de [átomos para una galería privada](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
- Distribuya un archivo .pkgdef que describa la galería privada. Se recomienda esta configuración para los administradores que desean conectar una galería privada a muchos equipos al mismo tiempo.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Agregar una galería privada a extensiones y actualizaciones en Visual Studio  
 Cuando hay una galería privada disponible, puede agregarla a **Extensiones y actualizaciones** en Visual Studio.  
  
 ![Cuadro de diálogo para agregar del Administrador de extensiones](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Para agregar una galería privada a Extensiones y actualizaciones  
  
1. En la barra de menús, elija **Herramientas**, **Opciones**.  
  
2. En el nodo **Entorno,** seleccione **Extensiones y actualizaciones**.  
  
3. Elija el botón **Agregar**.  
  
4. En el campo **Nombre,** escriba un nombre para `My Gallery`la galería privada, por ejemplo, .  
  
5. En el campo **Dirección URL,** escriba la dirección URL de la fuente Atom o el sitio de SharePoint que hospeda la galería privada.  
  
    1. Si el host es una fuente Atom que se conecta a `http://www.mywebsite/mygallery/atom.xml`la galería privada, la dirección URL se parecería a esta: .  Esta dirección URL puede hacer referencia a un archivo o a una ruta de acceso de red.  
  
    2. Si el host es un sitio de SharePoint, la dirección URL se parecería a este: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx`.  
  
### <a name="managing-private-galleries"></a>Gestión de galerías privadas  
 Un administrador puede poner una galería privada a disposición de varios equipos al mismo tiempo modificando el registro del sistema en cada equipo. Para ello, cree un archivo .pkgdef que describa las nuevas claves del Registro y sus valores.  El formato de este archivo es el siguiente.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Para obtener más información, consulte [Cómo: administrar una galería privada mediante](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)la configuración del Registro .  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Instalación de extensiones desde una galería privada  
 Puede buscar e instalar extensiones de Visual Studio desde una galería privada en **Extensiones y actualizaciones**. Los pasos siguientes utilizan `My Gallery`una galería privada denominada .  
  
 ![Administrador de extensiones instalando una galería privada](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Para buscar e instalar extensiones desde una galería privada  
  
1. En la barra de menús, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
2. En el panel izquierdo, seleccione **Extensiones en línea**y, a continuación, seleccione **Mi galería**.  
  
3. En el panel derecho, seleccione una extensión y, a continuación, elija el botón **Descargar.**  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Actualización de extensiones desde una galería privada  
 A medida que se publican nuevas versiones de las extensiones de Visual Studio en la galería privada, puede actualizar las extensiones que ha instalado. Los pasos siguientes utilizan `My Repository`una galería privada denominada .  
  
 ![Actualización de la galería privada del Administrador de extensiones](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Para actualizar una extensión instalada desde una galería privada  
  
1. En la barra de menús, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
2. En el panel izquierdo, seleccione **Actualizaciones**y, a continuación, seleccione **Mi repositorio**.  
  
3. En el panel derecho, seleccione una extensión y, a continuación, elija el botón **Actualizar.**  
  
## <a name="see-also"></a>Consulte también  
 [Búsqueda y uso de extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Suministro de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
