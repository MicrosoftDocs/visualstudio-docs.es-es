---
title: Caché de esquema del Editor XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 574de335bdc7be6cbef658009645efbd6bc6620d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53886272"
---
# <a name="schema-cache"></a>Caché de esquema

El Editor XML proporciona una caché de esquema que se encuentra en la *%InstallRoot%\Xml\Schemas* directory. La caché de esquema es global para todos los usuarios de un equipo e incluye esquemas XML estándar que se utilizan en IntelliSense y en la validación de documentos XML.

El editor XML también puede encontrar los esquemas ubicados en la solución, los esquemas especificados en el **esquemas** campo del documento **propiedades** ventana y los esquemas identificados por el `xsi:schemaLocation` y `xsi:noNamespaceSchemaLocation`atributos.

En la siguiente tabla se describen los esquemas que están instalados con el Editor XML.


| Filename | Descripción |
|-| - |
| *Catalog.xsd* | Esquema para archivos de catálogo de esquema del Editor XML. Para obtener información acerca de los catálogos de esquema, consulte a continuación. |
| *DotNetConfig.xsd* | Esquema para archivos Web.Config, "<http://schemas.microsoft.com/.NETConfiguration/v2.0>". |
| *MSBuild.xsd* | Esquema para los archivos make de MSBuild, "<http://schemas.microsoft.com/developer/msbuild/2003>". |
| *msdata.xsd* | Esquema para las anotaciones XSD que agrega la clase <xref:System.Data.DataSet>, "urn:schemas-microsoft-com:xml-msdata". |
| *msxsl.xsd* | Esquema para las extensiones de bloque de script XSLT de Microsoft, urn:schemas-microsoft-com:xslt. |
| *SnippetFormat.xsd* | Esquema para los archivos XML de fragmento de código. Para obtener ejemplos, vea *%InstallDir%\VC#\Expansions*. |
| *Soap1.1.xsd* | Esquema de Simple Object Access Protocol (SOAP) 1.1, http://schemas.xmlsoap.org/soap/envelope/. |
| *Soap1.2.xsd* | Esquema para el Protocolo simple de acceso a objetos (SOAP) 1.2. |
| *SiteMapSchema.xsd* | Esquema de archivo XML de mapa del sitio ASP.NET, "<http://schemas.microsoft.com/AspNet/SiteMap-File-1.0>". |
| *WSDL.xsd* | Esquema de lenguaje de descripción de servicios Web, http://schemas.xmlsoap.org/wsdl/. |
| *xenc.xsd* | Esquema para el cifrado XML, http://www.w3.org/2000/09/xmldsig#. |
| *XHTML.xsd* | Esquema de XHTML http://www.w3.org/1999/xhtml. |
| *xlink.xsd* | Esquema para XLink1.0, http://www.w3.org/1999/xlink. |
| *XML.xsd* | Esquema que describe atributos XML: space y XML: lang, http://www.w3.org/XML/1998/namespace. |
| *xmlsig.xsd* | Esquema para firmas digitales XML, http://www.w3.org/2000/09/xmldsig#. |
| *XSDSchema.xsd* | Esquema que describe el propio, XSD http://www.w3.org/2001/XMLSchema. |
| *XSLT.xsd* | Esquema para transformaciones XML, http://www.w3.org/1999/XSL/Transform. |

## <a name="update-schemas-in-the-cache"></a>Actualizar los esquemas en la memoria caché
 El editor carga el directorio de la caché de esquema cuando se carga el paquete del Editor XML y está atento a los cambios durante la ejecución. Si se ha agregado un esquema, se carga automáticamente en un índice de esquemas conocidos almacenado en memoria. Si se ha quitado un esquema, se quita automáticamente del índice almacenado en memoria. Si se actualiza un esquema, se invalida automáticamente la caché almacenada en memoria de este esquema.

> [!NOTE]
> Como el directorio de la caché de esquema es global en el equipo, aquí solo debe agregue esquemas que sean estándares y que resulten de utilidad para todos los proyectos de Visual Studio que se puedan crear en el equipo.


 El Editor XML también admite un número cualquiera de archivos de catálogo de esquema en el directorio de la caché de esquema. Los catálogos de esquema pueden apuntar a otras ubicaciones de esquemas que desea que el editor siempre conozca. El *catalog.xsd* archivo define el formato del archivo de catálogo y se incluye en el directorio de caché de esquema. El *catalog.xml* archivo es el catálogo predeterminado y contiene vínculos a otros esquemas en el *% InstallDir %*. El siguiente es un muestreo de la *catalog.xml* archivo:

```xml
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%InstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%InstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%InstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

 El atributo `href` puede ser cualquier ruta de acceso de archivo o dirección URL http que apunte al esquema. La ruta de acceso del archivo puede ser relativa al documento de catálogo. El editor reconoce las siguientes variables, delimitadas por %%, que se expandirán en la ruta de acceso:

-   InstallDir

-   System

-   ProgramFiles

-   Programas

-   CommonProgramFiles

-   ApplicationData

-   CommonApplicationData

-   LCID

El documento de catálogo puede incluir un elemento `Catalog`, que apunta a otros catálogos. Puede utilizar el elemento `Catalog` para apuntar a un catálogo central que comparte su equipo o empresa, o a un catálogo en línea que comparten sus asociados de negocios. El atributo `href` es la ruta de acceso de archivo o la dirección URL http de los otros catálogos. A continuación se muestra un ejemplo del elemento `Catalog`:

```xml
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

 El catálogo también puede controlar el modo en que los esquemas se asocian con documentos XML mediante el elemento especial `Association`. Este elemento asocia esquemas que carecen de un espacio de nombres de destino con una extensión de archivo determinada, lo cual puede ser de utilidad dado que el Editor XML no realiza ninguna asociación automática de esquemas que no tienen un atributo `targetNamespace`. En el siguiente ejemplo el elemento `Association` asocia el esquema dotNetConfig con todos los archivos que tienen la extensión "config":

```xml
<Association extension="config" schema="%InstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>Esquemas traducidos
 En muchos casos el *catalog.xml* archivo no contiene entradas para los esquemas traducidos. Puede agregar entradas adicionales para la *catalog.xml* archivo que apunte al directorio de esquemas traducidos.

 En el siguiente ejemplo, se crea un nuevo elemento `Schema` y usa la variable %LCID% para apuntar al esquema traducido.

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="change-the-location-of-the-schema-cache"></a>Cambiar la ubicación de la caché de esquema

Puede personalizar la ubicación de la caché de esquema mediante el **varios** página de opciones. Si dispone de un directorio de esquemas favoritos, se puede configurar el editor para que en su lugar utilice esos esquemas.

> [!NOTE]
> Este cambio solo afecta al usuario actual de Visual Studio.

### <a name="to-change-the-schema-cache-location"></a>Para cambiar la ubicación de la caché de esquema

1.  Desde el **herramientas** menú, seleccione **opciones**.

2.  Expanda **Editor de texto**, expanda **XML**y, a continuación, haga clic en **varios**.

3.  Haga clic en el **examinar** situado en la **esquemas** campo.

4.  Seleccione la carpeta para la caché de esquema y haga clic en **Aceptar**.

### <a name="to-add-another-directory-of-common-schemas"></a>Para agregar otro directorio de esquemas comunes

1.  Editar el *catalog.xml* archivo en el directorio de caché de esquema de editor de XML.

2.  Agregue un nuevo elemento `<Catalog href="..."/>` que apunte al directorio de esquemas adicionales.

3.  Guarde los cambios.

     El catálogo se recarga automáticamente.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)