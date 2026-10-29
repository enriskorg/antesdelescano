# Antes del escaño

Clasificación de los 350 diputados de la XV Legislatura del Congreso de los Diputados según la experiencia previa que declaran en el **apartado I de su declaración de intereses económicos**. Ese apartado recoge las actividades desarrolladas en los cinco años anteriores a la obtención del mandato.

La aplicación (`index.html`) muestra el reparto general y por grupo parlamentario, y un listado filtrable con la ficha de cada diputado. Cada ficha incluye el texto extraído y el enlace a la declaración original en congreso.es.

## Población

- 137 diputados que siguen en la Diputación Permanente.
- 213 diputados que cesaron con la disolución de las Cámaras (06/10/2026).

No se incluyen las bajas producidas a lo largo de la legislatura.

## Categorías

| Categoría | Criterio |
|---|---|
| **Experiencia profesional** | Declara al menos una actividad en el sector privado o un puesto público no político (funcionario, docente, personal sanitario, magistrado, personal laboral). Puede combinarla con cargos políticos. |
| **Solo política o designación** | Todo lo declarado son cargos electos, cargos de gobierno o de libre designación (ministro, consejero, director general, delegado, jefe de gabinete, asesor o personal eventual), o cargos y empleos en partidos. |
| **Sin experiencia declarada** | El apartado está vacío o declara «ninguna». |

Dentro de la experiencia profesional se distinguen tres marcas: privada, pública no política, y si además se declaran cargos políticos.

## Datos

`data/clasificacion.csv` (separador `;`, UTF-8) contiene, por diputado:

- formación, grupo parlamentario, circunscripción y situación;
- la categoría asignada y un resumen de lo declarado;
- las dudas de clasificación (ver abajo);
- la fecha y el número de versiones de la declaración;
- el enlace al PDF y el texto obtenido por OCR del apartado I.

## Método

1. Se descargó la versión más reciente de cada declaración desde congreso.es.
2. Los PDF son escaneos: el apartado I se extrajo con OCR (Tesseract, modelo en español).
3. Cada declaración se clasificó leyendo ese texto. Las declaraciones vacías o ilegibles se revisaron sobre la imagen.
4. En los 31 diputados con varias versiones se revisaron también las anteriores. En tres casos la última versión es una modificación que no repite el apartado I y se usó la anterior.

## Limitaciones

- **Ventana de cinco años.** El formulario solo pide lo ocurrido en los cinco años previos al mandato, y solo lo que pueda condicionar la actividad política o haya dado ingresos. «Solo política» significa «solo política en esa ventana», no a lo largo de la carrera.
- **Periodos recortados.** Muchos diputados fechan su actividad desde 2018, el inicio de la ventana, aunque la ejercieran desde antes. Por eso no se puede medir la duración de la experiencia profesional: un periodo corto puede ser real o estar recortado por el formulario.
- **Autodeclaración.** Los datos no están verificados por terceros, y el nivel de detalle varía mucho de unos diputados a otros.
- **OCR.** Puede haber errores de lectura, sobre todo en declaraciones manuscritas. Cada ficha enlaza al original para comprobarlo.

## Dudas de clasificación

Los casos marcados en la columna `dudas` aplican un criterio provisional:

| Código | Situación | Criterio aplicado |
|---|---|---|
| `PARTIDO` | Empleo o asesoría en un partido o grupo parlamentario | Se cuenta como experiencia política. |
| `DESIG` | Puesto directivo que puede ser de libre designación o técnico | Se decide caso a caso. |
| `EXC` | Funcionario en servicios especiales o excedencia | Se cuenta como experiencia pública no política. |
| `JUB` | Jubilado o retirado | Se decide caso a caso. |
| `FECHA` | Actividad fuera de la ventana o posterior a la elección | Se cuenta igualmente. |
| `MENOR` | Actividad no política marginal | Se decide caso a caso. |
| `SINDICAL` | Cargo o empleo sindical | Se cuenta como profesional por el empleo de base. |
| `REMITE` | No detalla y remite a otras declaraciones | Se clasifica según lo que menciona. |
| `VERSION` | Clasificado con una versión anterior de la declaración | — |

## Fuente

Congreso de los Diputados, Registro de Intereses, declaraciones de intereses económicos (XV Legislatura): <https://www.congreso.es/busqueda-de-diputados>
