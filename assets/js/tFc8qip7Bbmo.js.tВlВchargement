var responseJson;
var combo;
var caminoName;
var str1;
var str2;
var res;
var myLatitude;
var centrosCity;
var myLongitude;
var center;
var centrosTown;
var localizacion;
var codsINE;
var codsINETemp;
var infomacionAsociadaCamino;
var parametroNombre;
var baseUrlPin = "https://gis.dgt.es/mapa/iconos/";
var baseUrlInterna = "/.content/.assets/img/mapa/";
var milisecondsChangeZone = 3000;
var allowedImgExtensions = /(.jpg|.jpeg|.png|.gif|.ico|.svg|.bmp)$/i;
var allowedAudioExtensions = /(.mp3|.wav|.ogg)$/i;
var allowedFileExtensions = /(.pdf|.xls|.xlsx|.dox|.docx|.ppt|.pptx|.pps|.ppsx|.zip|.rar|.7z)$/i;
var jefaturasExtra;
var colaboradoresTipoElemento = {
	'JP':{'capa':'JEFATURA'},
	'JEFATURA':{'tipo_elemento':'JP'},
	'CG':{'capa':'Centros_gestion'},
	'Centros_gestion':{'tipo_elemento':'CG'},
	'CE':{'capa':'Centros_ejecutivos'},
	'Centros_ejecutivos':{'tipo_elemento':'CE'}, 
	'AV':{'capa':'Asociacion_victimas'},
	'Asociacion_victimas':{'tipo_elemento':'AV'},
	'CGT':{'capa':'CGT'},
	'CGT':{'tipo_elemento':'CGT'},
	'EVENTO':{'capa':'EVENTO'},
	'AUTOESCUELA':{'capa':'AUTOESCUELA'},
	'CATV':{'capa':'CATV'},
	'CRC':{'capa':'CRC'},
	'AYU':{'capa':'Ayuntamientos_DGT'},
	'TALLER':{'capa':'Talleres'},
	'ITV':{'capa':'ITV'},
	'Tramos_motos_puntos':{'capa':'Tramos_motos_puntos'},
	'OPE_puertos':{'capa':'OPE_puertos'},
	'OPE_descanso':{'capa':'OPE_descanso'},
	'OPE_informacion':{'capa':'OPE_informacion'},
	'Areas_servicio':{'capa':'Areas_servicio'},
	'Salidas':{'capa':'Salidas'},
	'Entradas':{'capa':'Entradas'},
	'Junquera_Total':{'capa':'Junquera_Total'},
	'Irun_Total':{'capa':'Irun_Total'},
	'stars':{'capa':'CustomPoints'},
	'safetytunes':{'capa':'CustomPoints'},
	'escaperoom':{'capa':'CustomPoints'},
	'caminoescolar':{'capa':'CustomPoints'},
	'juegoserpiente':{'capa':'CustomPoints'},
	'PUNTO':{'capa':'PUNTO'}
};
const medallas = ["","Medalla de Oro", "Medalla de Plata", "Medalla de Bronce", "Sin medalla"];
const medalla = ["","Oro", "Plata", "Bronce", "Sin medalla"];
var colaboradoresPlantilla = $.trim($('#colaboradoresPlantilla').html());
var listadoColaboradoresPlantilla = $.trim($('#listadoColaboradoresPlantilla').html());
var listadoColaboradoresPlantillaAV = $.trim($('#listadoColaboradoresPlantillaAV').html());
var movilidadPlantilla = $.trim($('#movilidadPlantilla').html());
var plantillaCamara = $.trim($('#camarasPlantilla').html());
var listadoDesplazamientosPlantilla = $.trim($('#listadoDesplazamientosPlantilla').html());
var listadoMotosPlantilla = $.trim($('#listadoMotosPlantilla').html());
var listadoPuntoOPE = $.trim($('#listadoPuntoOPE').html());
var listadoPuntoOPP = $.trim($('#listadoPuntoOPP').html());
var listadoPuntoStars = $.trim($('#listadoPuntoStars').html());
var listadoPuntoSafetytunes = $.trim($('#listadoPuntoSafetyTunes').html());

function genRankingTable(data){
	var rows = '';
	$.each(data.stages, function (index, obj) { 
		mjeDebug("index="+index+" || obj="+obj.nombre)
		if(parametrosMapa.tipoElementoCustomPoints == "new-stars" || parametrosMapa.tipoElementoCustomPoints == "new-stars-historico"){
			//TODO para	new-stars y new-stars-historico
			rows += '<tr><td>' + obj.nombre_centro + '</td><td>' + obj.poblacion + '</td>';
			let valorMedalla = obj.l2 != '' ? obj.l2 : '4';
			rows +=	'<td>' + (obj.l1 != '' ? obj.l1 : '') + '</td><td class="medalla medalla-' + valorMedalla + '"><span style="opacity: 0;">' + valorMedalla + '</span><span>' + medallas[valorMedalla] + '</span></td>';
		}else if(responseJson[obj.codigo_centro] != undefined){
			rows += '<tr><td>' + obj.nombre + '</td><td>' + obj.municipio + '</td>';
			let valorMedalla = responseJson[obj.codigo_centro].medalla != '' ? responseJson[obj.codigo_centro].medalla : '4';
			rows +=	'<td>' + (responseJson[obj.codigo_centro].puntuacion != '' ? responseJson[obj.codigo_centro].puntuacion : '') + '</td><td class="medalla medalla-' + valorMedalla + '"><span style="opacity: 0;">' + valorMedalla + '</span><span>' + medallas[valorMedalla] + '</span></td>';
		} else {
			rows +=	'<td>X</td><td>X</td>';	/* X para detectar que no hay código de colegio correcto */
		}
		rows +=	'</tr>';
	});
	//si acaban existiendo mas de 1 tabla hacer un generador de tablas que permita customizacion
	var table = '<div class="table-filter"><table class="table w-100"><thead><tr><th>Centro</th><th>Provincia (Población)</th><th>Puntos</th><th>Medalla</th></tr></thead><tbody>';
		table += rows;
		table += '</tbody><tfoot></tfoot></table></div>';
	
	$(".list-mode .list p").text("Ranking");
	$("#accordionDataMap").parent().append(table);
	
	 $('.table-filter .table').DataTable({
	        "searching": true,
	        "paging": true,
	        "columnDefs": [
	            { "width": "31%", "targets": 0 },
	            { "width": "86px", "targets": -2 },
	            /*{ className: "text-center", "targets": -1 }*/
	        ],
	        /*columnDefs: [
	           {
	                targets: [2],
	                orderData: [2, 3],
	            },
	            {
	                targets: [3],
	                orderData: [3, 2],
	            },
	        ],*/
	        "language": {
	            "url": '/.content/.assets/json/spanish.json'
	        },
	        rowReorder: {
	            selector: 'td:nth-child(2)'
	        },
	        colReorder: false,
	        responsive: true,
	        order: [[3, 'asc'], [2, 'desc']],
	        initComplete: function () {
	        }

	    });
	 	
	 	$(".list-mode a").on("click",function(e){
			if($(".list-mode a.list").hasClass("active")){
				$(".topSidebar .form-group").hide();
				$(".dataTables_length").hide();
				$("#accordionDataMap").hide();
			} else {
				$(".topSidebar .form-group").show();
				$("#accordionDataMap").show();
			}
	 	});
}


function genStructure(mode){
	/*
	Para el mapa de Planes territoriales
	description:
		arg mode = 0 para generar la estructura en modo lista
		arg mode vacio genera la estructura de sidebar la de por defecto
	*/
	
	var ccaa = [
		['1', 'Andalucía'],
		['2', 'Aragón'],
		['3', 'Principado de Asturias'],
		['4', 'Islas Baleares'],
		['5', 'Canarias'],
		['6', 'Cantabria'],
		['7', 'Castilla y León'],
		['8', 'Castilla la Mancha'],
		['9', 'Cataluña'],
		['10', 'Comunidad Valenciana'],
		['11', 'Extremadura'],
		['12', 'Galicia'],
		['13', 'Madrid'],
		['14', 'Región de Murcia'],
		['15', 'Navarra'],
		['16', 'País Vasco'],
		['17', 'La Rioja'],
		['18', 'Ceuta'],
		['19', 'Melilla']
	];
	
	var datos_ccaa = [];
	var estructura = '';
	for(var i=0; i<ccaa.length; i++){
		
		for(var j=0; j<2; j++){
			datos_ccaa.push(ccaa[i][j]);
		}
		
		var cod_ccaa = datos_ccaa[0];
		var nombre_ccaa = datos_ccaa[1];
		var fatherCard_dataParent= '#CCAA';
		
		if(mode==0){
			cod_ccaa += "_lista";
			var id_accordeon_lista = $(".listadoColaboradores .accordion .accordion").attr("id");
			fatherCard_dataParent = "#"+id_accordeon_lista;
		}
		

		estructura += ''
		+'<div class="card d-none" data-id="'+cod_ccaa+'">'
		
			+'<div class="card-header" id="heading-autonomico-'+cod_ccaa+'">'
				+'<div class="title"><button class="btn btn-link collapsed" type="button" data-toggle="collapse" data-target="#collapse-autonomico-'+cod_ccaa+'" aria-expanded="false" aria-controls="collapse-autonomico-'+cod_ccaa+'">'+nombre_ccaa+'<i class="fas fa-chevron-down"></i><i class="fas fa-chevron-up"></i></button></div>'
			+'</div>'
			
			+'<div id="collapse-autonomico-'+cod_ccaa+'" class="collapse" aria-labelledby="heading-autonomico-'+cod_ccaa+'" data-parent="'+fatherCard_dataParent+'">'
			
				+'<div class="card-body">'
					+'<div class="accordion" id="planes'+cod_ccaa+'">'
					
						+'<div class="card d-none" data-id="CCAA">'
							+'<div class="card-header" id="heading-autonomico'+cod_ccaa+'">'
								+'<div class="title"><button class="btn btn-link collapsed" type="button" data-toggle="collapse" data-target="#collapse-autonomico'+cod_ccaa+'" aria-expanded="false" aria-controls="collapse-autonomico'+cod_ccaa+'">Planes autonómicos<i class="fas fa-chevron-down"></i><i class="fas fa-chevron-up"></i></button></div>'
							+'</div>'
							+'<div id="collapse-autonomico'+cod_ccaa+'" class="collapse" aria-labelledby="heading-autonomico'+cod_ccaa+'" data-parent="#planes'+cod_ccaa+'">'
								+'<div class="card-body">'
									+'<ul class="resources plans">'
										
									+'</ul>'
								+'</div>'
							+'</div>'
						+'</div>'
						
						+'<div class="card d-none" data-id="provincial">'
							+'<div class="card-header" id="heading-provincial'+cod_ccaa+'">'
								+'<div class="title"><button class="btn btn-link collapsed" type="button" data-toggle="collapse" data-target="#collapse-provincial'+cod_ccaa+'" aria-expanded="false" aria-controls="collapse-provincial'+cod_ccaa+'">Planes provinciales<i class="fas fa-chevron-down"></i><i class="fas fa-chevron-up"></i></button></div>'
							+'</div>'
							+'<div id="collapse-provincial'+cod_ccaa+'" class="collapse" aria-labelledby="heading-provincial'+cod_ccaa+'" data-parent="#planes'+cod_ccaa+'">'
								+'<div class="card-body">'
									+'<ul class="resources plans">'
										
									+'</ul>'
								+'</div>'
							+'</div>'
						+'</div>'
						
						+'<div class="card d-none" data-id="local">'
							+'<div class="card-header" id="heading-local'+cod_ccaa+'">'
								+'<div class="title"><button class="btn btn-link collapsed" type="button" data-toggle="collapse" data-target="#collapse-local'+cod_ccaa+'" aria-expanded="false" aria-controls="collapse-local'+cod_ccaa+'">Planes locales<i class="fas fa-chevron-down"></i><i class="fas fa-chevron-up"></i></button></div>'
							+'</div>'
							+'<div id="collapse-local'+cod_ccaa+'" class="collapse" aria-labelledby="heading-local'+cod_ccaa+'" data-parent="#planes'+cod_ccaa+'">'
								+'<div class="card-body">'
									+'<ul class="resources plans">'
										
									+'</ul>'
								+'</div>'
							+'</div>'
						+'</div>'
						
					+'</div>'
				+'</div>'
			+'</div>'
		+'</div>';
		
		//clear
		datos_ccaa = [];
	}
	
	return estructura;
}

function fillStructure(){
	/*Para el mapa de planes territoriales*/
	
	//insert structure in page
	var estructura = genStructure();
	$(".sidebar .accordion").append(estructura);
	//rompemos el collapse en el sidebar
	$(".sidebar .accordion .accordion .card button").attr("data-target","");
	
	
	//generar la estructura de modo lista
	estructura = genStructure(0);
	//insertar structura en modo lista TODO: y cambiar el id del heading para que no coincida con el del sidebar
	$(".listadoColaboradores .maps-accordion .accordion").append(estructura);
	
	//fill structure with data
	$.each(responseJson, function(i, planesTerritorios){
		//planes y territorios CCAA, provinciales, locales
		var territorio = i;
		$(planesTerritorios).each(function(i, planesTerritorio){
			//planes en un territorio
			var cod_ccaa = planesTerritorio.ID;
			var data = '';
			
			$(planesTerritorio.datos).each(function(i, plan){
				//titulo del plan
				data += ''
				+'<li class="list-group-item maps">'
					+'<p class="description">' + plan.titulo + '</p>';
				
				$(plan.datos).each(function () {
					//datos del plan
					data += ''
						+'<div class="list-group-maps">'
							+'<p>' + this.titulo + '</p>'
							+'<div class="link">'
								+'<span class="file-info ' + this.tipo + '"></span> '
								+'<a href="' + this.enlace + '" class="icon-external-link" target="_blank">'
									+'<span class="sr-only">link externo</span>'
								+'</a>'
							+'</div>'
						+'</div>';
				});
				data += '</li>';
			});
			
			//insertar la data en su respectivo lugar
			$("#planes"+cod_ccaa+" .card[data-id="+territorio+"] .plans").append(data);
			$("#planes"+cod_ccaa+"_lista .card[data-id="+territorio+"] .plans").append(data);
			
			//donde se haya insertado la data quitar el d-none
			$("#planes"+cod_ccaa+" .card[data-id="+territorio+"]").removeClass("d-none");
			$("#planes"+cod_ccaa+"_lista .card[data-id="+territorio+"]").removeClass("d-none");
			
			$(".sidebar .accordion .card[data-id="+cod_ccaa+"]").removeClass("d-none");
			$(".listadoColaboradores .maps-accordion .accordion .card[data-id="+cod_ccaa+"_lista]").removeClass("d-none");
		});
		
	});
	
}

function isEventPage() {
	if ($(".tipo-evento").length) {
		if ($(".mapa").length) {
			$(".card-link.icon-location").show();
			$(".card-link.icon-location").click(function (e) {
				e.preventDefault();
				goToAnchor($(".mapa"));
			});
			mostrarInfoMapa();
		}
	}
}

function mostrarInfoMapa() {
	if (tamVentana()[0] > 767) {
		$(document).on("scroll", function (e) {
			var inicioMapa = $(".mapa").offset().top;
			var calculoSaltaEvento = $(".mapa").offset().top - ((parseInt(tamVentana()[1] / 3) * 2));
			mjeDebug("Sigue activo")
			if ($(window).scrollTop() > calculoSaltaEvento) {
				$(document).off("scroll");
				setTimeout(function () {
					$(".map .sidebar").addClass("open");
					//retardo para pintar el punto en el mapa para asegurarnos que el centrado automatico del iframe se carga primero
					if($(".tipo-evento").length){
                        ubicate(eventos.mapa.mapCoord.longitud, eventos.mapa.mapCoord.latitud, baseUrlPin + "pin-seleccionado.svg", eventos.mapa.mapZoom);
                    } else {// mapa tipo punto
                        ubicate(puntos.mapa.mapCoord.longitud, puntos.mapa.mapCoord.latitud, baseUrlPin + "pin-seleccionado.svg", puntos.mapa.mapZoom);
						if ($(".mapa").length) {
							displayInfoMap(puntos, "evento", puntos);
							let infoMapa = $(".map .sidebar");
							loadMapInfo(infoMapa, "complejo", puntos, "datosPunto");
						}
                    }
					
				}, 1000);
			}
		});
	}
}



/* let CONSTANTS = {
	CGT: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CGT/FeatureServer/0",
	ITV: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/ITV/FeatureServer/0",
	AUTOESCUELA: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/AUTOESCUELA/FeatureServer/0",
	CATV: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CATV/FeatureServer/0",
	CRC: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CRC/FeatureServer/0",
	JEFATURA: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/JEFATURA/FeatureServer/0",
	Limite_admin_prov: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/Limite_admin_prov/FeatureServer/0",
	Limite_admin_ccaa: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/Limite_admin_ccaa/FeatureServer/0",
	Tramos_motos_lineas: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/100_Tramos_motos/FeatureServer/0",
	Tramos_motos_puntos: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/100_Tramos_motos/FeatureServer/1",

	POI_Frances: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/1",
	Traza_Frances: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/2",
	Tramos_Frances: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/3",

	POI_Norte: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/5",
	Traza_Norte: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/6",
	Tramos_Norte: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/7",

	POI_Plata: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/9",
	Traza_Plata: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/10",
	Tramos_Plata: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/11",

	POI_Sureste: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/13",
	Traza_Sureste: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/14",
	Tramos_Sureste: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/15",

	POI_Madrid: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/17",
	Traza_Madrid: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/18",
	Tramos_Madrid: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/19",

	POI_Ebro: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/21",
	Traza_Ebro: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/22",
	Tramos_Ebro: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/23",

	POI_Catalan: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/25",
	Traza_Catalan: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/26",
	Tramos_Catalan: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/27",

	POI_Jaume: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/29",
	Traza_Jaume: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/30",
	Tramos_Jaume: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/31",

	POI_Ingles: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/33",
	Traza_Ingles: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/34",
	Tramos_Ingles: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/35",

	POI_Fisterra: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/37",
	Traza_Fisterra: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/38",
	Tramos_Fisterra: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/39",

	POI_Portugues: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/41",
	Traza_Portugues: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/42",
	Tramos_Portugues: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/CaminosDeSantiago/FeatureServer/43",

	Rutas_bicicletas: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/arcgis/rest/services/rutas_bicicletas/FeatureServer/0",    // seguras
	Rutas_ciclisas_seguras: "https://services3.arcgis.com/TXNiwnLDifb5lMaR/arcgis/rest/services/rutas_ciclisas_seguras/FeatureServer/0"       // protegidas

	
}

let arrayCaminoSantiago = [];

const arrayLayersURLs = Object.entries(CONSTANTS);

var esri = Esri();

var map = esri.createMap();

var mapView = esri.createView(map, "mapa");

for (var i = 0; i < arrayLayersURLs.length; i++) {
	var layer = esri.createFeatureLayer(arrayLayersURLs[i][1]);
	map = esri.addFeatureLayer(map, layer);
	// Si es una capa del camino de Santiago, se usa el titulo que viene en Constants
	// Si no, se procede como hasta ahora con el título de la capa
	if (layer.title.indexOf('CaminosDeSantiago') != -1) {
		arrayLayersTitle[i] = [arrayLayersURLs[i][0], layer];
		arrayCaminoSantiago.push([arrayLayersURLs[i][0], arrayLayersURLs[i][1]]);
		//Capa lineas
	} else if (layer.title.indexOf('100 Tramos') != -1) {
		if ((layer.url + "/" + layer.layerId).indexOf("/FeatureServer/0") != -1) {
			arrayLayersTitle[i] = [layer.title.split(' ').join('_').replace('100_Tramos_motos', 'Tramos_motos_lineas'), layer];
			//Capa puntos
		} else {
			arrayLayersTitle[i] = [layer.title.split(' ').join('_').replace('100_Tramos_motos', 'Tramos_motos_puntos'), layer];
		}
	} else {
		arrayLayersTitle[i] = [layer.title.split(' ').join('_'), layer];
	}

	layer.visible = false;
} */


function getJSON(url) {
	$.getJSON(url, function (json) {
		responseJson = json;
		// this will show the info it in firebug console
	});
}
$(".sidebar .complejo .close").click(function (e) {
	$(this).parents(".sidebar").removeClass("open");
});


function getGPS() {
	if ($(".mapa").length) {
		localizacion = new Object();
		localizacion.error = true;
		if (navigator.geolocation) {
			navigator.geolocation.getCurrentPosition(function (objPosition) {
				/*var lat = objPosition.coords.latitude;		//Longitud en grados decimales
				var lon = objPosition.coords.longitude;			//Latitud en grados decimales
				var accuracy = objPosition.coords.accuracy;		//Precisión en metros
				var timestamp = objPosition.timestamp;			//Momento de la toma de estos datos
				var altitude = objPosition.coords.altitude;		//Altitud en metros
				var altitudeAccuracy = objPosition.coords.altitudeAccuracy;		//Precisión de la altitud en metros
				var heading = objPosition.coords.heading;		//Orientación en grados decimales en el sentido de las agujas del reloj
				var speed = objPosition.coords.speed;			//Velocidad en metros/segundo	
				*/
				var d = new Date();
				d.setTime(objPosition.timestamp);
				localizacion.objPosition = objPosition;
				localizacion.error = false;
				myLatitude = localizacion.objPosition.coords.latitude;
				myLongitude = localizacion.objPosition.coords.longitude;
				$(".geolocalizacion-link").removeClass("d-none");
				
			}, function (objPositionError) {
				switch (objPositionError.code) {
					case objPositionError.PERMISSION_DENIED:
						localizacion.mje = "No se ha permitido el acceso a la posición del usuario.";
//						alert("Permiso GPS DENEGADO")
						setTimeout(function(){
							getGPS();
							centerUserPosition();
						},2000);
						

						break;
					case objPositionError.POSITION_UNAVAILABLE:
						localizacion.mje = "No se ha podido acceder a la información de su posición.";
						break;
					case objPositionError.TIMEOUT:
						localizacion.mje = "El servicio ha tardado demasiado tiempo en responder.";
						break;
					default:
						localizacion.mje = "Error desconocido.";
				}
			}, {
				maximumAge: 75000,
				timeout: 15000
			});
		} else {
			localizacion.mje = "Su navegador no soporta la API de geolocalización.";
		}
		
	}
}

function switchMap() {
	//listener de cambio modo lista modo mapa
	$(".list-mode a").on("click",function(e){
		e.preventDefault();
		$(".list-mode a").removeClass("active");
		$(this).addClass("active");
		if($(".list-mode a.list").hasClass("active")){
			//hide map
			$(".map").addClass("d-none");//hide map
			$(".mt-5.list-view.container").removeClass("d-none");
			$(".container.full-width-container.views").removeClass("full-width-container");
			$(".maps-list-out").removeClass("d-none");
			$(".context-list").removeClass("d-none");
			$(".listadoColaboradores").removeClass("d-none");//show list
			//si el mapa tiene checkboxes pasar el estado de los checks al otro modo
			if($(".maps-checkbox").length == 2){
				var checkboxes = $(".maps-checkbox")[0];
				var checkboxes_mapa = $("input", checkboxes);
				
				//ver si el main checkbox tiene estado neutro/indeterminado	
				var main_indeterminate = false;
				if($(checkboxes_mapa[0]).hasClass("indeterminate")){
					main_indeterminate = true;
					$(checkboxes_mapa[0]).prop("indeterminate", false);
				}
				
				//recojer el estado de los checkboxes
				var estados = [];
				for(var i=0; i<checkboxes_mapa.length; i++){
					var checkbox_mapa = checkboxes_mapa[i];
					estados.push(checkbox_mapa.checked);
				}
				
				//actualizar los estados de los checkboxes en el otro modo
				var checkboxes = $(".maps-checkbox")[1];
				var checkboxes_mapa = $("input", checkboxes);
				for(var i=0; i<checkboxes_mapa.length; i++){
					var checkbox_mapa = checkboxes_mapa[i];
					checkbox_mapa.checked = estados[i];
				}
				
				//si el main checkbox tiene estado neutro/indeterminado actualizar en el otro lado
				if(main_indeterminate){
					$(checkboxes_mapa[0]).prop("indeterminate", true);
				}
			}
			
		} else {
			//show map
			$(".map").removeClass("d-none");
			$(".mt-5.list-view.container").addClass("d-none");
			$(".container.views").addClass("full-width-container");
			$(".maps-list-out").addClass("d-none");
			$(".listadoColaboradores").addClass("d-none");//hide list
			//si el mapa tiene checkboxes pasar el estado de los checks al otro modo
			if($(".maps-checkbox").length == 2){
				var checkboxes = $(".maps-checkbox")[1];
				var checkboxes_mapa = $("input", checkboxes);
				
				//ver si el main checkbox tiene estado neutro/indeterminado	
				var main_indeterminate = false;
				if($(checkboxes_mapa[0]).hasClass("indeterminate")){
					main_indeterminate = true;
					$(checkboxes_mapa[0]).prop("indeterminate", false);
				}
				
				//recojer el estado de los checkboxes
				var estados = [];
				for(var i=0; i<checkboxes_mapa.length; i++){
					var checkbox_mapa = checkboxes_mapa[i];
					estados.push(checkbox_mapa.checked);
				}
				
				//actualizar los estados de los checkboxes en el otro modo
				var checkboxes = $(".maps-checkbox")[0];
				var checkboxes_mapa = $("input", checkboxes);
				for(var i=0; i<checkboxes_mapa.length; i++){
					var checkbox_mapa = checkboxes_mapa[i];
					checkbox_mapa.checked = estados[i];
				}
				
				//si el main checkbox tiene estado neutro/indeterminado actualizar en el otro lado
				if(main_indeterminate){
					$(checkboxes_mapa[0]).prop("indeterminate", true);
				}
			}
			
		}
	});
}

function openFilter() {
	var buttonFilter = $(".btn.btn-outline-primary.filterSantiago");
	var santiagoPopUp = $(".santiagoPopUp");
	$(buttonFilter).click(function () {
		if ($(santiagoPopUp).hasClass("d-none")) {
			$(santiagoPopUp).removeClass("d-none");
		} else {
			$(santiagoPopUp).addClass("d-none");
		}
	});
}


function changeZoom(location, miliseconds) {
	var buttonMap = $(".canarias-link i");
	if ($(buttonMap).hasClass("icon-dgt-canarias-vector")) {
		location = "peninsula";
	} else {
		location = "canarias";
	}
	sendMessageToIframe(["changeCenter", location, miliseconds]);

}
/*
function changeButtonMap() {
	$(".canarias-link i").click(function () {
		if ($(this).hasClass("icon-dgt-canarias-vector")) {
			$(".canarias-link i").removeClass("icon-dgt-canarias-vector");
			$(".canarias-link i").addClass("icon-dgt-peninsula-vector");
		} else {
			$(".canarias-link i").removeClass("icon-dgt-peninsula-vector");
			$(".canarias-link i").addClass("icon-dgt-canarias-vector");
		}
	});
}*/
var roads = []; //variable global para guardar todas las carreteras de una provincia
function dropdownCenters() {
	$(".form-group .custom-select").change(function () {
		$(".sidebarDetail").removeClass("open");
		if (this.className == "custom-select  provinciaMap") {
			var checkeds = $(".maps-checkbox input:checked");
			centro = parametrosMapa.mapLayer;
			if(stages_caller=="jefaturas"){
				centrosCity = $(".form-group .custom-select.provinciaMap option:selected");
				centrosCityProvid = centrosCity[0].attributes["data-provid"].value;
				//el get cities falla por que recibe multiples capas
				//getCities(centro, centrosCityProvid);

				var lugar = centrosCity[0].attributes[5].value;
				var cod_ine = cod_ine = $('.custom-select.provinciaMap').find(":selected")[0].dataset.provid;
				var datos_combo = [lugar, cod_ine]
				renderStages(datos_combo, json_stages.stages, "Limite_admin_prov");
				
				centrosCityValue = centrosCity.attr("objectid-prov");
				centerElement("Limite_admin_prov", centrosCityValue, 10);
				
				return;
			}
			if (centro.includes(",")) {
				parametrosMapa.mapLayer.split(",").forEach(function (mapLayer, index) {
					centrosCity = $(".form-group .custom-select.provinciaMap option:selected");
					if (mapLayer != "Rutas_bicicletas" && mapLayer != "Rutas_ciclisas_seguras") {
						centrosCityValue = centrosCity.attr("data-provid");		//centrosCityValue = centrosCity[0].attributes["data-provid"].value;
						if(centrosCityValue == undefined){
							//si selecciona en el combobox "mostrar todas las provincias" quitar todos los d-none
							$(".sidebar .accordion .card").removeClass("d-none");
							$(".listadoColaboradores .maps-accordion .accordion .card").removeClass("d-none");
							sendMessageToIframe(["changeCenter", "peninsula", milisecondsChangeZone]);
						} else{
							//getCenters(mapLayer, centrosCityValue, '-', colaboradoresTipoElemento[mapLayer].tipo_elemento);	//devuleve solo el listado de elementos de esa zona, tanto en mapa como en listado
							centerElement("Limite_admin_prov", centrosCity[0].attributes["objectid-prov"].value, 10);
							//getCities(mapLayer, centrosCityValue);
							getRoads(mapLayer, centrosCityValue);
							
							//filtrar por provincias, conseguir codigo INE seleccionado en el combobox
							let cod_ine = $('.custom-select.provinciaMap').find(":selected")[0].dataset.provid;
							if(cod_ine){
								//poner un d-none en todos los elementos de lista y acordeon
								$(".sidebar .accordion .card").addClass("d-none");
								$(".listadoColaboradores .maps-accordion .accordion .card").addClass("d-none");
								
								//quitar el d-none de los elementos que tengan el mismo codigo INE
								$(".sidebar .accordion .card[data-codine="+cod_ine+"]").removeClass("d-none");
								$(".listadoColaboradores .maps-accordion .accordion .card[data-codine="+cod_ine+"]").removeClass("d-none");
								
								//comprobar las checkbox
								
								//detectar de que grupo de checkbox
								var esta_lista = false
								var esta_lista = $(".list-mode .list").hasClass("active");
								var all_checkboxes = $(".maps-checkbox .input-checkbox[type='checkbox']:not('.first-checkbox')");
								var checkboxes;
								if(esta_lista){
									//segunda mitad
									var half_length = all_checkboxes.length/2;
									var checkboxes = all_checkboxes.splice(half_length,all_checkboxes.length);
								}else{
									//primera mitad
									var half_length = all_checkboxes.length/2;
									var checkboxes = all_checkboxes.splice(0,half_length);
								}
								var diccionario = {
									"checkbox_value":"data-tipoelemento",
									"Centros_gestion":"CG",
									"Asociacion_victimas":"AV",
									"Centros_ejecutivos":"CE",
									"JEFATURA":"JP",
									"CGT":"CGT",
									"Ayuntamientos_DGT":"AYU",
									"CRC":"CRC",
									"AUTOESCUELA":"AUTOESCUELA",
									"ITV":"ITV",
									"CATV":"CATV",
									"Talleres": "TALLER"
								};
									
								for(var i=0; i<checkboxes.length; i++){
									var ckbox = checkboxes[i];
									var cambiar_capa = $(ckbox).val();
									var capa = diccionario[cambiar_capa];
									if(ckbox.checked == false){
										//checkbox desactivado -> se esconden los elementos que correspanda
										$(".sidebar .accordion .card[data-tipoelemento="+capa+"]").addClass("d-none");
										$(".listadoColaboradores .accordion .card[data-tipoelemento="+capa+"]").addClass("d-none");
									}
								}
								
							}
						}
					} else {
						centrosName = centrosCity[0].attributes["data-nameprov"].value;
						getRoads("Rutas_bicicletas", centrosName);
						centerElement("Limite_admin_prov", centrosCity[0].attributes["objectid-prov"].value, 10);
					}
				});
				console.log(roads);
				setRoadsProvincia(roads);//llamo con todas las roads acumuladas
				roads = []; //reinicio la variable global roads (l. 274)
			} else {
				centrosCity = $(".form-group .custom-select.provinciaMap option:selected");
				centrosCityValue = centrosCity.attr("objectid-prov");		//centrosCity[0].attributes["objectid-prov"].value		//centrosCityValue = centrosCity[0].attributes["data-provid"].value;
				if(centrosCityValue == "sin-datos"){
					//si selecciona en el combobox "mostrar todas las provincias" quitar todos los d-none
					$(".sidebar .accordion .card").removeClass("d-none");
					$(".listadoColaboradores .maps-accordion .accordion .card").removeClass("d-none");
					sendMessageToIframe(["changeCenter", "peninsula", milisecondsChangeZone]);
				} else {
					centerElement("Limite_admin_prov", centrosCityValue, 10);
					if (parametrosMapa.mapLayer != "Rutas_ciclisas" && parametrosMapa.mapLayer != "Rutas_bicicletas" && parametrosMapa.mapLayer != "Rutas_ciclisas_seguras") {
						centrosCityProvid = centrosCity[0].attributes["data-provid"].value;
						
						
						var lugar = centrosCity[0].attributes[5].value;
						var cod_ine = cod_ine = $('.custom-select.provinciaMap').find(":selected")[0].dataset.provid;
						var datos_combo = [lugar, cod_ine]
						renderStages(datos_combo, json_stages.stages, "Limite_admin_prov");
						
						
						//filtrar por provincias
						//conseguir codigo INE seleccionado en el combobox
						cod_ine = $('.custom-select.provinciaMap').find(":selected")[0].dataset.provid;
						if(cod_ine){
							//poner un d-none en todos los elementos de lista y acordeon
							$(".sidebar .accordion .card").addClass("d-none");
							$(".listadoColaboradores .maps-accordion .accordion .card").addClass("d-none");
							//quitar el d-none de los elementos que tengan el mismo codigo INE
							$(".sidebar .accordion .card[data-codine="+cod_ine+"]").removeClass("d-none");
							$(".listadoColaboradores .maps-accordion .accordion .card[data-codine="+cod_ine+"]").removeClass("d-none");
						}
					} else {
						centrosName = centrosCity[0].attributes["data-nameprov"].value;
						getRoads("Rutas_bicicletas", centrosName);
					}
				}
			}
		}
		if (this.className == "custom-select towns") {
			if (centro.includes(",")) {
				parametrosMapa.mapLayer.split(",").forEach(function (mapLayer, index) {
					centrosTown = $(".form-group .custom-select.towns option:selected");
					centrosCityValue = centrosCity[0].attributes["data-provid"].value;
					getCenters(mapLayer, centrosCityValue, centrosTown[0].value, '-');
				});
			}
			centrosTown = this.value;
			
			//centramos en el municipio
			var cod_ine = $(".form-group .custom-select.towns option:selected")[0].attributes.cod_ine.value;
			toggleLayer("Limite_admin_muni");
			centerElementByCodIne("Limite_admin_muni", cod_ine, 13);	
			toggleLayer("Limite_admin_muni");
			//provincia
			var lugar = centrosCity[0].attributes[5].value;
			//municipio
			var lugar_muni = $(".form-group .custom-select.towns option:selected")[0].attributes.value.value;
			var datos_combo = [lugar_muni, cod_ine];
			if(parametrosMapa.mapLayer == 'AUTOESCUELA' && datos_combo[0] == "Hospitalet de Llobregat, L"){
				datos_combo[0] = "L HOSPITALET DE LLOBREGAT";
			}
			renderStages(datos_combo, json_stages.stages, "Limite_admin_muni");
			
		}
	});
}

function capitalizeFirstLetter(string) {
	string = string.toLowerCase(string);
	return string.charAt(0).toUpperCase() + string.slice(1);
}

function centerUserPosition() { /*ver si cambiar por la siguiente funcion*/
	//si el mapa es de eventos no preguntar por la localizacion
	if (!$(".tipo-evento").length || !puntos) {
		setTimeout(function(){	/* delay para asegurarnos que el mapa/puntos estan cargados */
			if (localizacion) {
				if (localizacion.error) {
					mjeDebug("localizacion no inicializada");
				} else {
					let zoom = localizacion.objPosition.mapZoom == undefined ? '11' : localizacion.objPosition.mapZoom;
					ubicate(localizacion.objPosition.coords.longitude, localizacion.objPosition.coords.latitude, baseUrlPin + "pin-seleccionado.svg", zoom);
					mjeDebug("Resultado: <br>" + "Long = " + localizacion.objPosition.coords.longitude + "<br>Lat = " + localizacion.objPosition.coords.latitude + "<br>precisión = " + localizacion.objPosition.coords.accuracy + "m" + "<br>zoom = " + zoom);
					
					//Hacer query ajax rellenar provincia
					var latitud = localizacion.objPosition.coords.latitude;
					var longitud = localizacion.objPosition.coords.longitude;
					getGPSLocationInfo("Limite_admin_prov", latitud, longitud);
				}
		
			} else {
				mjeDebug("localizacion no inicializada");
			}
		},2000);
	}
}

function myLocation() {
	centro = parametrosMapa.mapLayer;
	if (myLongitude && myLatitude) {
		findPointsInRadius(centro, myLongitude, myLatitude, 30000);
		ubicate(myLongitude, myLatitude, baseUrlPin + "pin-seleccionado.svg", 10);
	}
}
/*
//se limpia el html que hubiera previamente
$(".sidebar.open .accordion").html(listado);
$(".accordion.dataMap .accordion").html(listado);
*/
function renderStages(gps_location_info, stages, capa){
	if(!stages){
		mjeDebug("json_stages no inicializado, puede que sea un mapa que no muestra listados");
		return;
	}
	
	//filtramos todos los stages y nos quedamos solo con los que coinciden con la GPS_info
	var lugar_gps;
	var codINE_gps;
	if(gps_location_info.features){
		//si el gps esta activado sacar la localizacion de ahi
		lugar_gps = gps_location_info.features[0].attributes.NAMEUNIT;
		codINE_gps = gps_location_info.features[0].attributes.COD_INE;
	}else{
		//si no tiene gps activado sacar la informacion de los filtros del combobox
		lugar_gps = gps_location_info[0];
		codINE_gps = gps_location_info[1];
	}
	var mapa_custom = "";
	if(parametrosMapa.tipoElementoCustomPoints){
		mapa_custom = parametrosMapa.tipoElementoCustomPoints;
	}
	var mapa_custom_aceptados = ["stars","stars-historico","new-stars","new-stars-historico","safetytunes","escaperoom","caminoescolar","juegoserpiente"];
	if(mapa_custom_aceptados.includes(mapa_custom)){
		var listado = "";
		switch(capa){
			case "Limite_admin_prov":
				var idParent = $(".accordion.dataMap .accordion").attr("id");
				for(var i=0; i<stages.length; i++){
					var stage = stages[i];
					//seleccionar solo los stages que coincidan por lugar
					if(stage.cod_ine_prov.trim() == codINE_gps){
						listado += renderDataMapTemplate(stage, "listado", i, idParent);
					}
				}
				//se pone en el combobox de provincias la provincia seleccionada o el lugar_gps
				$(" .custom-select.provinciaMap option[data-provid=" +codINE_gps+ "] ").prop('selected', true);
				
				//se hace el getCities para mostrar en el combo de municipios los que tenga la provincia
				centrosCity = $(".form-group .custom-select.provinciaMap option:selected");
				centrosCityProvid = centrosCity[0].attributes["data-provid"].value;
				centro = parametrosMapa.mapLayer;
				getCities(centro, centrosCityProvid);
				break;
				
			case "Limite_admin_muni":
				var idParent = $(".accordion.dataMap .accordion").attr("id");
				for(var i=0; i<stages.length; i++){
					var stage = stages[i];
					//seleccionar solo los stages que coincidan por lugar
					console.log("stage_cod: "+stage.codigo_postal+" ,muni_cod: "+codINE_gps);
					
					if(stage.hasOwnProperty("cod_ine_muni")){
						//cuando el getStages tenga este nuevo campo en los objetos se podra hacer el filtrado por aqui
						if(stage.codigo_postal == codINE_gps){
							console.log("aguacate");
							listado += renderDataMapTemplate(stage, "listado", i, idParent);				
						}
					}else{
						//mientras tanto filtramos comparando los nombres, esto tendra algunos casos 
						//en los que el filtrado no coincida aun siendo el mismo nombre ej: 
						//"La Rioja; Rioja, La" este caso fallaria	
						var nombre_combo = parseToId(lugar_gps.trim());
						var nombre_stage = parseToId(stage.municipio.trim());
						if(nombre_stage == nombre_combo){
							listado += renderDataMapTemplate(stage, "listado", i, idParent);
						}
						
					}
					
				}
				break;
				
			case "Limite_admin_ccaa":
				var idParent = $(".accordion.dataMap .accordion").attr("id");
				for(var i=0; i<stages.length; i++){
					var stage = stages[i];
					//seleccionar solo los stages que coincidan por lugar
					if(stage.cod_ine == codINE_gps){
						listado += renderDataMapTemplate(stage, "listado", i, idParent);
					}
				}
				break;
				
			default:
				mjeDebug("Error renderStages, capa no existe");
		}
	}//else if(mapa_custom == "new-stars" || mapa_custom == "new-stars-historico"){
		//TODO
		//return;
	else{
		var listado = "";
		switch(capa){
			case "Limite_admin_prov":
				var idParent = $(".accordion.dataMap .accordion").attr("id");
				for(var i=0; i<stages.length; i++){
					var stage = stages[i];
					//seleccionar solo los stages que coincidan por lugar
					if(stage.cod_ine == codINE_gps){
						listado += renderDataMapTemplate(stage, "listado", i, idParent);
					}
				}
				//se pone en el combobox de provincias la provincia seleccionada o el lugar_gps
				$(" .custom-select.provinciaMap option[data-provid=" +codINE_gps+ "] ").prop('selected', true);
				
				//se hace el getCities para mostrar en el combo de municipios los que tenga la provincia
				centrosCity = $(".form-group .custom-select.provinciaMap option:selected");
				centrosCityProvid = centrosCity[0].attributes["data-provid"].value;
				centro = parametrosMapa.mapLayer;
				getCities(centro, centrosCityProvid);
				break;
				
			case "Limite_admin_muni":
				var idParent = $(".accordion.dataMap .accordion").attr("id");
				for(var i=0; i<stages.length; i++){
					var stage = stages[i];
					//seleccionar solo los stages que coincidan por lugar
					console.log("stage_cod: "+stage.codigo_postal+" ,muni_cod: "+codINE_gps);
					
					if(stage.hasOwnProperty("cod_ine_muni")){
						//cuando el getStages tenga este nuevo campo en los objetos se podra hacer el filtrado por aqui
						if(stage.codigo_postal == codINE_gps){
							listado += renderDataMapTemplate(stage, "listado", i, idParent);				
						}
					}else{
						//mientras tanto filtramos comparando los nombres, esto tendra algunos casos 
						//en los que el filtrado no coincida aun siendo el mismo nombre ej: 
						//"La Rioja; Rioja, La" este caso fallaria	
						var nombre_combo = parseToId(lugar_gps.trim());
						var nombre_stage = parseToId(stage.municipio.trim());
						if(nombre_stage == nombre_combo){
							listado += renderDataMapTemplate(stage, "listado", i, idParent);
						}
						
					}
					
				}
				break;
				
			case "Limite_admin_ccaa":
				var idParent = $(".accordion.dataMap .accordion").attr("id");
				for(var i=0; i<stages.length; i++){
					var stage = stages[i];
					//seleccionar solo los stages que coincidan por lugar
					if(stage.cod_ine == codINE_gps){
						listado += renderDataMapTemplate(stage, "listado", i, idParent);
					}
				}
				break;
				
			default:
				mjeDebug("Error renderStages, capa no existe");
		}
	}
	
	//despues de tener los stages seleccionados hay que renderizarlos en el html
	//if(listado != ""){
		//modo mapa
		let map_id = $(".accordion.dataMap .accordion").attr('id');
		let listado_sidebar = replaceAll(listado, map_id, map_id + '_sidebar');
		$(".sidebar.open .accordion").html(listado_sidebar);
		
		//cambios para adaptar listado a sidebar
		$(".sidebar .card-header button").removeAttr("data-toggle");
		$(".sidebar .accordion .collapse").removeAttr("id");
		
		/*TODO: aqui en el mapa de stars en vez de modo lista hay que hacer modo ranking*/
		//modo listado
		listado = listado.replace(/{{templ_col_9}}/ig, 'col-md-9');
		listado = listado.replace(/{{templ_col_6}}/ig, 'col-md-6');
		listado = listado.replace(/{{templ_col_2}}/ig, 'col-md-2');
		$(".accordion.dataMap .accordion").html(listado);
		
		//quitamos los collapse del modo mapa para no tener html repetido
		if($(".accordion_ccaa").length == 0){
			//si no es el mapa de estrategias y planes
			$(".map .card .collapse").remove();
		}
	//}
	
	//
}

function getGPSLocationInfo(capa, latitud, longitud){
	/*	
	Partiendo de la latitud y longitud retorna el nombre del lugar y el codigo ine de esa lugar
	lugar = provincia/municipio/ccaa, el lugar se puede cambiar con el parametro capa
	
	
	url prueba
	var url = "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/Limite_admin_prov/"+
	"FeatureServer/0/query?where=1%3D1&objectIds=&time=&geometry=-5.517360%2C42.609250&geometryType="+
	"esriGeometryPoint&inSR=4326&spatialRel=esriSpatialRelIntersects&resultType=none&distance=1&unit"+
	"s=esriSRUnit_Meter&returnGeodetic=false&outFields=nameunit%2Ccod_ine&returnGeometry=false&retur"+
	"nCentroid=false&featureEncoding=esriDefault&multipatchOption=xyFootprint&maxAllowableOffset=&ge"+
	"ometryPrecision=&outSR=&defaultSR=&datumTransformation=&applyVCSProjection=false&returnIdsOnly="+
	"false&returnUniqueIdsOnly=false&returnCountOnly=false&returnExtentOnly=false&returnQueryGeometr"+
	"y=false&returnDistinctValues=false&cacheHint=false&orderByFields=&groupByFieldsForStatistics=&o"+
	"utStatistics=&having=&resultOffset=&resultRecordCount=&returnZ=false&returnM=false&returnExceed"+
	"edLimitFeatures=true&quantizationParameters=&sqlFormat=none&f=pjson&token=";
	*/

	var url = "https://services3.arcgis.com/TXNiwnLDifb5lMaR/ArcGIS/rest/services/"+capa+"/"+
	"FeatureServer/0/query?where=1%3D1&objectIds=&time=&geometry="+longitud+"%2C"+latitud+"&geometryType="+
	"esriGeometryPoint&inSR=4326&spatialRel=esriSpatialRelIntersects&resultType=none&distance=1&unit"+
	"s=esriSRUnit_Meter&returnGeodetic=false&outFields=nameunit%2Ccod_ine&returnGeometry=false&retur"+
	"nCentroid=false&featureEncoding=esriDefault&multipatchOption=xyFootprint&maxAllowableOffset=&ge"+
	"ometryPrecision=&outSR=&defaultSR=&datumTransformation=&applyVCSProjection=false&returnIdsOnly="+
	"false&returnUniqueIdsOnly=false&returnCountOnly=false&returnExtentOnly=false&returnQueryGeometr"+
	"y=false&returnDistinctValues=false&cacheHint=false&orderByFields=&groupByFieldsForStatistics=&o"+
	"utStatistics=&having=&resultOffset=&resultRecordCount=&returnZ=false&returnM=false&returnExceed"+
	"edLimitFeatures=true&quantizationParameters=&sqlFormat=none&f=pjson&token=";
	
	if(!json_stages){
		mjeDebug("Error json_stages no inicializado");
		return;
	}
	
	$.ajax({
		url: url,
		dataType : 'json',
		success: function(data){
			renderStages(data, json_stages.stages, capa);
		},
		error: function( jqXHR, textStatus, errorThrown ) {
			mjeDebug( 'Error: ' + textStatus );
		}
	});

}

function getDatosPlanesTerritoriales(){
	$.ajax({
		url: "/.content/.assets/json/Planes-Territoriales.json",
		dataType : 'json',
		success: function(data){
			responseJson=data;
			json_stages=data;
			fillStructure();
		},
		error: function( jqXHR, textStatus, errorThrown ) {
			mjeDebug( 'Error: ' + textStatus );
		}
	});
}

function mapas() {
	// mjeDebug("FUNCTION MAPAS");
	if(parametrosMapa.mapLayer.split(",").length == 4){
		stages_caller = "jefaturas"
	}
	
	if ($(".map").length) {
		parametrosMapa.mapLayer.split(",").forEach(function (mapLayer, index) {
			// mjeDebug(index + ":" + mapLayer);
			switch (mapLayer) {
				case "camino_Frances":
				case "camino_Norte":
				case "camino_Sureste":
				case "camino_Plata":
				case "camino_Madrid":
				case "camino_Ebro":
				case "camino_Catalan":
				case "camino_Jaume":
				case "camino_Ingles":
				case "camino_Fisterra":
				case "camino_Portugues":
					$("a[data-peligrosidad]").click(function(e){
						anclaTramoOPuntoPeligroso(e, $(this));
					});
					caminos(mapLayer,parametrosMapa.mapLayerName);
					break;
				case "Ayuntamientos_DGT":
				case "Talleres":
				case "JEFATURA":
				case "CRC":
				case "CATV":
				case "ITV":
				case "CAMINOSANTIAGO":
				case "CGT":
				case "AUTOESCUELA":
				case "Asociacion_victimas":
				case "Centros_ejecutivos":
				case "Centros_gestion":
				case "camaras_web":
				case "Radares_tramo":
				case "Radares_punto":
				case "OPE_puertos":
				case "OPE_informacion":
				case "OPE_descanso":
					toggleLayer(mapLayer);
					getStages(mapLayer);
					if (mapLayer == "Radares_punto"){
						toggleLayer("Radares_tramo_punto");
					}
					
					break;
				case "Tramos_motos_puntos":
					toggleLayer(mapLayer);
					getStages(mapLayer);
					if (mapLayer == "Tramos_motos_puntos")
						toggleLayer("Tramos_motos_lineas");
					break;
				case "Planes-Territoriales":
					setColor('Limite_admin_ccaa', 'rgba(0, 255, 0, 0)', 'rgba(0, 87, 166, 1)')
					setHighlightColor('#0099DA'); // RGB --> #0099DA --> 0,156,220
					toggleLayer("Limite_admin_ccaa");
					getDatosPlanesTerritoriales();
					break;
				case "Limite_admin_ccaa":
				case "Limite_admin_prov":
				case "Limite_admin_muni":			 
					setColor(mapLayer, 'rgba(0, 255, 0, 0)', 'rgba(0, 87, 166, 1)');
					setHighlightColor('#0099DA');
					toggleLayer(mapLayer);
					break;
				case "EVENTOS":
					if ($(".mapa").length) {
						displayInfoMap(eventos, "evento", eventos);
						let infoMapa = $(".map .sidebar");
						loadMapInfo(infoMapa, "complejo", eventos, "datosPunto")
					}
					break;
				case "Rutas_ciclisas_seguras":
				case "Corredor_central":
				case "Corredor_central_A2":
				case "Corredor_mediterraneo":
				case "Corredor_R2":
				case "Corredor_R4":
				case "Corredor_via_plata":
					toggleLayer(mapLayer);
					break;
				case "Rutas_bicicletas":
					toggleLayer(mapLayer);
					break;
				case "PUNTO":
					if ($(".mapa").length)
						ubicate(parametrosMapa.mapCoord.longitud, parametrosMapa.mapCoord.latitud, baseUrlPin + "pin-seleccionado.svg", parametrosMapa.mapZoom);
					break;
				case "CIFRAS":
					setColor(mapLayer, 'rgba(0, 255, 0, 0)', 'rgba(0, 87, 166, 1)')
					setHighlightColor('#0099DA');
					toggleLayer("Limite_admin_prov");
					setMultipleSelectionColor([0, 87, 166])
					setMultipleSelection(true);
					break;
				case "CGT":
					mjeDebug("click CGT, sin datos");
					break;
				case "Desplazamientos_visual":
					toggleLayer(parametrosMapa.formatoCapaYDatos);
					sendJsonCGT(parametrosMapa.formatoCapaYDatos);
					setTimeout(function(){
						sendMessageToIframe(["changeCenter", "peninsula", milisecondsChangeZone]);	//para que no se quede centrado en la ubicacion de la persona y se vean los datos del mapa
					},300);
					break;
				case "Desplazamientos_clic":
					toggleLayer(parametrosMapa.formatoCapaYDatos);
					sendJsonCGT(parametrosMapa.formatoCapaYDatos); 
					toggleLayer(parametrosMapa.formatoCapaYDatos); // necesario volver a quitarlo
					setTimeout(function(){
						sendMessageToIframe(["changeCenter", "peninsula", milisecondsChangeZone]);	//para que no se quede centrado en la ubicacion de la persona y se vean los datos del mapa
					},300);
					break;
				case "CustomPoints":
					toggleLayer(mapLayer);
					switch (parametrosMapa.tipoElementoCustomPoints) {
						case "stars":
						case "stars-historico":
						case "new-stars":
						case "new-stars-historico":
							starsAjax();
							break;
						case "safetytunes":
							var data = {tipo:"json",type:"POIGenerico",formato:"1",tipoelemento:"safetytunes"}
							ajaxCall("/.content/.assets/json/poi.json",data,"json","GET");
							break;
						case "escaperoom":
							var data = {tipo:"json",type:"POIGenerico",formato:"1",tipoelemento:"escaperoom"}
							ajaxCall("/.content/.assets/json/poi.json",data,"json","GET");
							break;
						case "caminoescolar":
							var data = {tipo:"json",type:"POIGenerico",formato:"1",tipoelemento:"caminoescolar"}
							ajaxCall("/.content/.assets/json/poi.json",data,"json","GET");
							break;
						case "juegoserpiente":
							var data = {tipo:"json",type:"POIGenerico",formato:"1",tipoelemento:"juegoserpiente"}
							ajaxCall("/.content/.assets/json/poi.json",data,"json","GET");
							break;
						default:
							console.log("mapa custom points no encontrado");
					}
					break;
				case "Areas_servicio":
				case "Salidas":
				case "Entradas":
				case "Junquera_Total":
				case "Irun_Total":
					toggleLayer(mapLayer);
					getStages(mapLayer);
					break;
				default:
					mjeDebug("Error en la configuración del mapa");
					break;
			}
		});
		centerUserPosition();
	}
}

function ajaxCall(url, data, dataType, method){
	$.ajax({
		url: url,
		data: data,
		dataType: dataType,
		method: method,
		success: function(data){
			//mapas custompoints esto sirve
			//en un futuro si esto quedara obsoleto
			//se podria utilizar otra variable para hacer la bifurcacion
			
			var mapa = parametrosMapa.tipoElementoCustomPoints;
			switch(mapa){
				case "juegoserpiente":
					juegoserpienteLogic(data);
					break;
				case "escaperoom":
					escaperoomLogic(data);
					break;
				case "caminoescolar":
					caminoescolarLogic(data);
					break;
				case "safetytunes":
					safetytunesLogic(data);
					break;
				default:
					console.log("ajaxCall caso no contemplado");
					break;
			}
		},
		error: function( jqXHR, textStatus, errorThrown ) {
			console.log( 'Error: ' + textStatus );
		}
	});
}

function juegoserpienteLogic(data){
	json_stages = data;
	addPointFromJson(json_stages.stages);
	inicializarDatosMadrid();
}
function escaperoomLogic(data){
	json_stages = data;
	addPointFromJson(json_stages.stages);
	inicializarDatosMadrid();
}
function caminoescolarLogic(data){
	json_stages = data;
	addPointFromJson(json_stages.stages);
	inicializarDatosMadrid();
}
function safetytunesLogic(data){
	json_stages = data;
	addPointFromJson(json_stages.stages);
	inicializarDatosMadrid();
}

function starsAjax(){
	if(parametrosMapa.tipoElementoCustomPoints == "stars"){
		getDatosMapaStars(0);
	}else if(parametrosMapa.tipoElementoCustomPoints == "stars-historico"){
		starsHistorico();
	}else if(parametrosMapa.tipoElementoCustomPoints == "new-stars"){
		//hay que obtener el curso actual
		//dentro de la llamada de este AJAX se llama al otro
		newStarsSelectAJAX("new-stars");
	}else if(parametrosMapa.tipoElementoCustomPoints == "new-stars-historico"){
		//se llama al ajax de colegios en el año actual 
		newStarsSelectAJAX("new-stars-historico");
	}
}

function newStarsAJAX(curso){
	$.ajax({
		url: "/.content/.assets/json/newStars.html",
		data: {
			tipo:"json",
			type:"POIGenerico",
			formato:"1",
			tipoelemento:"stars",
			callback:"rellamada",
			datos: curso
		},
		dataType : 'json',
		success: function(data){
			json_stages = data;
			addPointFromJson(json_stages.respuesta);
			//aqui tengo que modificar un poco la estructura de los datos para que funcione
			Object.defineProperty(json_stages, "stages", Object.getOwnPropertyDescriptor(json_stages, "respuesta"));
			delete json_stages["respuesta"];
			inicializarDatosMadrid();
			//hemos cambiado el nombre respuesta a stages
			genRankingTable(json_stages);
		},
		error: function( jqXHR, textStatus, errorThrown ) {
			mjeDebug( 'Error: ' + textStatus );
		}
	});
}

var curso_seleccionado = "";
function newStarsSelectAJAX(mapa){
	$.ajax({
		url: "/.content/.assets/json/newStars.html",
		data: {
			tipo:"json",
			type:"POIGenerico",
			formato:"1",
			tipoelemento:"stars",
			callback:"rellamada",
		},
		dataType : 'json',
		success: function(data){
			var cursos = data;
			
			if(mapa == "new-stars"){
				//para el inicio de stars
				var curso_actual = cursos.opciones[cursos.opciones.length-1].filtro;
				newStarsAJAX(curso_actual);
			}else if(mapa == "new-stars-historico"){
				//para el historico de stars
				
				if($(".filter .curso").length == 0){
					//iteramos las opciones
					var opciones = cursos.opciones;
					var opciones_html = "";
					for(var i=0; i<opciones.length; i++){
						var opcion = opciones[i].filtro;
						opciones_html += "<option value='"+opciones[i].filtro+"'>"+opciones[i].filtro+"</option>"; 
					}
					
					//hacemos el select
					var select_html = "";
					select_html = ""+
					"<div class='form-group'>"+
						"<label for='select-date'>Selecciona un curso</label>"+
						"<select class='custom-select curso'>"+
							opciones_html+
						"</select>"+
					"<div class='form-group'>";
					
					//insertamos el select en el html de la pagina
					$(".filter-group .filter").append(select_html);
					var select_curso = $(".filter-group .filter .curso");
					//seleccionamos por defecto la penultima opcion
					select_curso.val(cursos.opciones[cursos.opciones.length-2].filtro);
					curso_seleccionado = select_curso.value;
					//cargamos los datos del antepenultimo año
					newStarsAJAX(cursos.opciones[cursos.opciones.length-2].filtro);
				}
				
				//listener para el select de curso
				$(".filter .custom-select.curso").on("change", function() {
					//recargar iframe para borrar los puntos ya pintados
					curso_seleccionado = this.value;
					$("iframe.mapa").attr("src","https://gis.dgt.es/mapa");
				});
			}	
		},
		error: function( jqXHR, textStatus, errorThrown ) {
			mjeDebug( 'Error: ' + textStatus );
		}
	});
}

function getDatosMapaStars(intento){
	$.ajax({
		url: "/.content/.assets/json/stars.json",
		data: {
			tipo:"json",
			type:"POIGenerico",
			formato:"1",
			tipoelemento:"stars",
			cache: intento
		},
		dataType : 'json',
		success: function(data){
			json_stages = data;
			
			if(data.hasOwnProperty("error")){
				if(intento==5){
					console.log("numero de intentos agotado");
				}else{
					getDatosMapaStars(intento+1);
				}
			}else{
				//despues de recibir respuesta se llama al 2º ajax
				if(parametrosMapa.tipoElementoCustomPoints == "stars"){
					getDatosMapaStarsPuntuaciones();
				}else if(parametrosMapa.tipoElementoCustomPoints == "stars-historico"){
					//seleccionar el elemento que haya en el select box curso
					var curso = $(".curso").find(":selected").val();
					getDatosMapaStarsPuntuacionesHistorico(curso)
				}
				
				//por si queremos cargar todos los stages y no cargar desde combobox
				//loadAllStages(json_stages);
			}
			
			
		},
		error: function( jqXHR, textStatus, errorThrown ) {
			mjeDebug( 'Error: ' + textStatus );
		}
	});
}

function getDatosMapaStarsPuntuaciones(){
	$.ajax({
		url: "/.content/.assets/json/puntuacion.json",
		dataType : 'json',
		success: function(data){
			//json_stages es la tabla colegios que tiene todos los colegios que han entrado a Stars alguna vez
			//responseJson es la tabla de puntuaciones de este curso
			//hay que seleccionar los colegios que esten en la tabla de puntuaciones
   
			responseJson = data;
			json_stages.stages = reverseFindSchools(json_stages, responseJson);
			addPointFromJson(json_stages.stages);
			inicializarDatosMadrid();
			genRankingTable(json_stages);
		},
		error: function( jqXHR, textStatus, errorThrown ) {
			mjeDebug( 'Error: ' + textStatus );
		}
	});
}

function getDatosMapaStarsPuntuacionesHistorico(curso){
	var	url = "/.content/.assets/json/historico/puntuacion-"+curso+".json";
	$.ajax({
		url: url,
		dataType : 'json',
		success: function(data){
			responseJson = data;
			//stars-historico quitar del json principal los colegios que no coincidan
			json_stages.stages = reverseFindSchools(json_stages, responseJson);
			addPointFromJson(json_stages.stages);
			inicializarDatosMadrid();
			genRankingTable(json_stages);
		},
		error: function( jqXHR, textStatus, errorThrown ) {
			mjeDebug( 'Error: ' + textStatus );
		}
	});
}

function reverseFindSchools(schools, scores){
	//Las schools y las scores estan relacionadas por codigo_centro
	//buscamos desde scores a schools, retornamos las coincidencias
	var selected_schools = [];
	//bucle scores
		//seleccionamos codigo centro del score
		//bucle schools
			//si codigo centro coincide guardar en selected_schools
			
	//formato que tiene que tener selected_schools: selected_schools.stages[i]
	var schools = schools.stages;
	$.each(scores, function(codigo_centro, score) {
		for(var i=0; i<schools.length; i++){
			var school = schools[i];
			if(codigo_centro == school.codigo_centro){
				selected_schools.push(school);
			}
		}
	});
	
	return selected_schools;
}

function resize(){
	if($(".contenedorMapas").length){
		$( window ).resize(function() {
			calculoPosicionBotonesMapa();
		});
	}
}
/*Esta funcion se podria borrar*/
function calculoPosicionBotonesMapa(){
	if(getViewport() == "sm" || getViewport() == "xs"){
		$(".buttons-maps").css("right", "0px");
		//boton abrir cerrar sidebar
		//$(".icon-chevron.d-none.d-md-block").css("right","40px");
	} else {
		$(".buttons-maps").css("right", "0px");
		//boton abrir cerrar sidebar
		//$(".icon-chevron.d-none.d-md-block").css("right","1552px");
		
	}
}

function clickAcordeonSideMap(){
	$(".sidebar .accordion").on("click",".card-header button", function(e){
		centerIcoMap($(this).parents(".card"))
	});
}

function centerIcoMap(elem){
	let id = elem.attr("data-id");
	let zoom = 14;
	//mapa camino santiago
	if(elem.attr("data-type") == "poi"){
		centerElement('POI_' + elem.attr("data-label"), id, zoom);
	}
	else if(elem.attr("data-type") == "tramo"){
		centerElement('Puntos_' + elem.attr("data-label"), id, zoom);
	}else{
		//resto de mapas
		let elem_data = elem[0].dataset;
		if(!elem_data.tipoelemento){
			return;
		}
		var tipo = elem_data.tipoelemento;
		var tipos = ["JP","OPE_descanso","OPE_informacion","OPE_puertos","Salidas","Entradas","Areas_servicio"]
		if(id == "undefined" || tipos.includes(tipo)){
			id = elem.attr("data-objectid");
		}
		
		let mapLayer = colaboradoresTipoElemento[elem_data.tipoelemento].capa;
		centerElement(mapLayer, id, zoom);
	}
	
	
}

function horarios(){
	if ($(".map").length) {
		$.ajax({
			url: "/conoce-la-dgt/donde-estamos/jefaturas/jefaturas.datos",
			dataType : 'json',
			success: function(data){
				jefaturasExtra = data;
			},
			error: function( jqXHR, textStatus, errorThrown ) {
				mjeDebug( 'Error: ' + textStatus );
			}
		});
	}
}

function buscar_mapa(){
	//cojer el texto que haya escrito en el input
	var texto = $(".buscadorMapa").val();
	var cards_mapa = $(".sidebarMap .accordion .card").not(".d-none");
	var cards_lista = $(".listadoColaboradores .accordion .card").not(".d-none");
	
	if(texto == ''){
		//mostrar todas las cards
		$(cards_mapa).removeClass("d-none");
		$(cards_lista).removeClass("d-none");
	}
	
	
	//filtrar la lista del modo mapa
	for(var i = 0; i<cards_mapa.length; i++){
		//obtener titulo del card
		var card = cards_mapa[i];
		var titulo = $("h3 button", card).text();
		titulo = titulo.trim();
		
		//si el titulo del card tiene algo del texto que se encuentra en el buscador mostrar esa card
		if(titulo.includes(texto)){
			//mostrar card
			$(card).removeClass("d-none");
		}else{
			//esconder card
			$(card).addClass("d-none");
		}
	}
	
	//filtrar la lista del modo lista
	for(var i = 0; i<cards_lista; i++){
		//obtener titulo del card
		var card = cards_lista[i];
		var titulo = $("h3 button", card).text();
		
		//si el titulo del card tiene algo del texto que se encuentra en el buscador mostrar esa card
		if(titulo.includes(texto)){
			//mostrar card
			$(card).removeClass("d-none");
		}else{
			//esconder card
			$(card).addClass("d-none");
		}
	}
}


function map_event_listeners(){
	
	if(parametrosMapa.tipoElementoCustomPoints == "safetytunes" || parametrosMapa.tipoElementoCustomPoints == "escaperoom"){
		$(".sidebarDetail").on("click", ".img-hover-zoom", function(){
			$("#genericModal").addClass("vmp");
			var img = $(".sidebarDetail img.img-fluid").clone()[0];
			var titulo = $(".sidebarDetail .titulo p").text().trim();
			$("#genericModal .modal-title").text(titulo);
			$(".modal-dialog .modal-body").html(img);
		});
		$(".listadoColaboradores").on("click", ".img-hover-zoom", function(){
			$("#genericModal").addClass("vmp");
			var img = $(".listadoColaboradores .accordion .show img.img-fluid").clone()[0];
			var titulo = $(".btn-link", $(this).parents()[8]).text().trim();
			$("#genericModal .modal-title").text(titulo);
			$(".modal-dialog .modal-body").html(img);
		});
		$(".sidebarDetail , .listadoColaboradores").on("click", ".documento", function(){
			$("#genericModal").addClass("vmp");
			var path = $($("span", this)[1]).attr("data-img");
			var tipo = tipoDocumento(path);
			switch(tipo){
				case "imagen":
					var html_img = "<img src="+path+" style='width:100%'></img>";
					var titulo = $($("span", this)[1]).text()
					$(".modal-dialog .modal-body").html(html_img);
					$("#genericModal .modal-title").text(titulo);
					$("#genericModal").addClass("vmp");
					break;
				case "video":
					var html_video = ""+
					"<div class='video-youtube card-img' data-mostrarPie=''>"+
						"<iframe src='"+path+"' frameborder='0'"+
						        "allow='accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture'"+
						        "allowfullscreen=''>"+
						"</iframe>"+
					"</div>";
					var titulo = $($("span", this)[1]).text();
					$(".modal-dialog .modal-body").html(html_video);
					$("#genericModal .modal-title").text(titulo);
					$("#genericModal").addClass("vmp");
					if(reproductorAudio.audio != "" && !reproductorAudio.audio.paused){
						reproductorAudio.audio.pause();
					}
					break;
				case "pdf":
					break;
			}
			
			
			
		});
		
		if(parametrosMapa.tipoElementoCustomPoints == "safetytunes"){
			$(".map, .listadoColaboradores").on("mouseover", "a", function(){
				$("span.iconoTipo",this).addClass("hover-icono");
			});
			$(".map, .listadoColaboradores").on("mouseleave", "a", function(){
				$("span.iconoTipo",this).removeClass("hover-icono");
			});
		}
	}
	
	//listener chevron del sidebar normal
	$(".showSidebar").click(function () {
		//abrir cerrar sidebar
		$(".sidebar").toggleClass("open");
		
		//siempre que se abra o cierre el sidebar normal cerrar el sidebarDetail
		if($(".sidebarDetail").hasClass("open")){
			$(".sidebarDetail").removeClass("open");
		}
		
		//clase "open" hace el desplazamiento horizontal
		$(".icon-chevron.showSidebar").toggleClass("open");
		
		//rotar el chevron al abrir y cerrar
		if($(".sidebar.open")[0]){
			//abierto
			$(".icon-chevron.d-none.d-md-block").css("transform", "rotate(180deg)");
		}else{
			//cerrado
			$(".icon-chevron.d-none.d-md-block").css("transform", "rotate(0deg)");
		}
	});
	
	//listener chevron del sidebarDetail modo pantalla ordenador/portatil
	$(".hideSidebarDetail").children().click(function (){
		//cerrar sidebar detail
		$(".sidebarDetail").removeClass("open");
		$(".sidebarDetail").removeClass("d-block");
		$(".sidebarDetail").removeClass("d-none");
		//quitar icono seleccionado
		removeAllSelectedIcons();
	});
	
	//listener chevron del sidebarDetail modo pantalla movil
	$(".hideSidebarDetailMovil").click(function (){
		//cerrar sidebar detail
		$(".sidebarDetail").removeClass("open");
		setTimeout(function(){
			$(".sidebarDetail").removeClass("d-block");
			$(".sidebarDetail").removeClass("d-none");
		},300);
		//quitar icono seleccionado
		removeAllSelectedIcons();
	});
	
	
	//listener boton centrado de mapa
	$(".icon-dgt-geolocalizacion").click(function (){
		//ubicate(lon, lat, url, zoom)
		/*en el argumento 'url' va el svg que aparecera al centrar, si se deja vacio aparece un punto negro*/
		if(!localizacion.error){
			let lon = localizacion.objPosition.coords.longitude;
			let lat = localizacion.objPosition.coords.latitude;
			ubicate(lon, lat, '', 100);
		}else{
			getGPS();
		}
	});
	
	//Estos listeners no se aplican a el mapas de estrategias y planes
	if(typeof parametrosMapa !== 'undefined' && !parametrosMapa.mapLayer.includes("Planes-Territoriales")){
		//listeners botones del listado/acordeon del sidebar
		$(".sidebar").on( "click", ".card-header button" ,function() {
			//abrir sidebar con la informacion del card
			$(".sidebarDetail").toggleClass("open");
			
			//contenido del sidebarDetail se saca del modo lista
			//$(".sidebarDetail .titulo p").html($(this).text());	
			//$(".sidebarDetail .accordion").html($(".card-body",$(this).parents(".card")).html());
			
			//titulo del sidebarDetail
			$(".sidebarDetail .titulo p").html($(this).text());	
			
			//buscar el contenido por atributo data-id en el listadoColaboradores
			var data_id = $($(this).parents()[2]).attr("data-id");
			var card = $(".listadoColaboradores .accordion .card[data-id="+data_id+"]").first();
			var contenido = $(".card-body .row", card).first().html();
			
			//revertimos los estilos del listado
			contenido = $(contenido).removeClass("col-md-9 col-md-6 col-md-2");
			$(contenido).children().children().removeClass("col-md-9 col-md-6 col-md-2");
			
			//insertar contenido en el sidebarDetail TODO fix de los contenidos
			$(".sidebarDetail .accordion").html(contenido);
			
			/*let tipoelemento = $(".listadoColaboradores .accordion .card[data-id="+data_id+"]").first()[0].dataset.tipoelemento;
			let objectid = $(".listadoColaboradores .accordion .card[data-id="+data_id+"]").first()[0].dataset.objectid;
			let capa = colaboradoresTipoElemento[tipoelemento].capa;
			removeAllSelectedIcons();
			selectIconFromLayer(capa,objectid);*/
			
		});
		
		//hover sidebar
		$(".sidebar").on("mouseover", ".card", function() {
			let elem_data = $(this)[0].dataset;
			let capa = colaboradoresTipoElemento[elem_data.tipoelemento].capa;
			if(capa == "Junquera_Total" || capa == "Irun_Total"){
				return;
			}
			removeAllSelectedIcons();
			selectIconFromLayer(capa,elem_data.objectid);
		});
		$(".sidebar").on("mouseleave", ".card", function() {
			//removeAllSelectedIcons();
		});
	}else{
		//aqui se definen los event listeners que se apliquen especificamente al mapa de estrategias y planes
		$(".sidebar").on("click", ".accordion .accordion .card", function(){
			//insertar el contenido en el sidebarDetail
			$(".sidebarDetail .titulo p").html($(".card-header .title button", this).text());	
			$(".sidebarDetail .accordion").html($(".card-body .plans", this).html());
			
			//abrir sidebar con la informacion del card
			$(".sidebarDetail").toggleClass("open");
		});
	}
	
}

function inicializarDatosMadrid(){
	//setTimeout(function(){
	
	//Si no tiene gps activado y los stages estan cargados inicializar a Madrid
	var mapa = parametrosMapa.mapLayerNameIntro.split(",")[0];
	var mapa_custom = "";
	if(parametrosMapa.tipoElementoCustomPoints){
		mapa_custom = parametrosMapa.tipoElementoCustomPoints;
	}
	var mapa_custom_aceptados = ["stars","stars-historico","new-stars","new-stars-historico","safetytunes","escaperoom","caminoescolar","juegoserpiente"];
	if(( json_stages && ( (mapa == "OPE" || mapa == "OPP") ) && (!myLatitude) )){
		/*
			no ejecutar datos a madrid si se cumple:
			-json_stages no ha sido cargado
			-el mapa no tiene filtros ej: OPE, OPP
			-si los datos no son de vexiza ej: Stars
			-si el GPS ya fue activado
		*/
		return;
	}else if((mapa_custom_aceptados.includes(mapa_custom)) && (!myLatitude)){
		//los mapas que sean de CustomPoints y tengan filtros ej:Stars tienen que entrar por aqui
		//ya que el getGPSLocationInfo funciona solo para vexiza
		//el gps tiene que estar desactivado tambien
		
		//simular que se selecciona Madrid en el filtro
		$(".custom-select.provinciaMap option[data-provid='28']").attr('selected', 'selected');
		centerElement("Limite_admin_prov", "23", 10);
		
		
		centrosCity = $(".form-group .custom-select.provinciaMap option:selected");
		
		var lugar = centrosCity[0].attributes[5].value;
		var cod_ine = cod_ine = $('.custom-select.provinciaMap').find(":selected")[0].dataset.provid;
		var datos_combo = [lugar, cod_ine]
		renderStages(datos_combo, json_stages.stages, "Limite_admin_prov");

		return;
	}
	

	//en caso de que no tengan el gps activado inicializamos los datos a los de Madrid
	var latitud = "40.40706";
	var longitud = "-3.74512";
	getGPSLocationInfo("Limite_admin_prov", latitud, longitud);
	
	centerElement("Limite_admin_prov", "23", 10);
	
	//},2000);
}

function starsHistorico(){
	if(parametrosMapa.tipoElementoCustomPoints != "stars-historico"){
		return;
	}
	//insertar el select box en la pagina
	$.ajax({
		url: "/.content/.assets/json/historico/select.html",
		dataType : 'html',
		success: function(data){
			var html_select = data;
			$(".filter").append(html_select);
			
			$(".curso").on("change", function(){
				var curso = this.value;
				var url = "/.content/.assets/json/historico/puntuacion-"+curso+".json";
				location.href = "?curso="+curso;
			});
			
			var curso = getAllUrlParams().curso
			//poner como seleccionado ese curso
			if(curso){
				$(".curso").val(curso);
			}
			getDatosMapaStars(0);
		},
		error: function( jqXHR, textStatus, errorThrown ) {
			mjeDebug( 'Error: ' + textStatus );
		}
	});
}

$(function () {
	if ($(".map").length) {
		getGPS();
		dropdownCenters();
		switchMap();
		//changeButtonMap();
		openFilter();
		isEventPage();
		horarios();
		checksMaps();
		mainCheck();
		resize();
		clickAcordeonSideMap();
		map_event_listeners();
		//inicializarDatosMadrid();
	}
});

function borrarResultados() {
	$("#respuestaMapa").html("Resultado: <br>");
}


function actualizarCapasOPE(check, activar){
	if(check == "Corredor_central"){
		//corredor central tiene que tener activado R4
		if(!capas_ope.includes("central") && activar){
			//activar capa central
			capas_ope.push("central");
			if(!capas_ope.includes("a2")){
				toggleLayer("Corredor_R4");
			}
		}else if(capas_ope.includes("central") && !activar){
			//desactivar capa central
			if(!capas_ope.includes("a2")){
				//si la capa a2 esta quitada
				toggleLayer("Corredor_R4");
			}
			var index = capas_ope.indexOf("central");
			capas_ope.splice(index, 1); 
		}
	}else if(check == "Corredor_central_A2"){
		//corredor central a2 tiene que tener activado R4 Y R2
		if(!capas_ope.includes("a2") && activar){
			//activar capa a2
			capas_ope.push("a2");
			if(capas_ope.includes("central")){
				toggleLayer("Corredor_R2");
			}else{
				toggleLayer("Corredor_R4");
				toggleLayer("Corredor_R2");
			}
		}else if(capas_ope.includes("a2") && !activar){
			//desactivar capa a2
			if(capas_ope.includes("central")){
				toggleLayer("Corredor_R2");
			}else{
				toggleLayer("Corredor_R4");
				toggleLayer("Corredor_R2");
			}
			var index = capas_ope.indexOf("a2");
			capas_ope.splice(index, 1); 
		}
	}else{
		//si entra aqui es porque se ha pulsado el boton de activar/desactivar todos
		if(!activar){
			//todas las capas han sido desactivadas previamente
			if(!capas_ope.includes("central") && !capas_ope.includes("a2")){
				//aqui ya han sido desactivadas
				toggleLayer("Corredor_R4");
				toggleLayer("Corredor_R2");
			}else if(capas_ope.includes("central") && !capas_ope.includes("a2")){
				//A2 desactivado
				toggleLayer("Corredor_R2");
			}
			capas_ope = [];
		}else{
			capas_ope.push("central");
			capas_ope.push("a2");
		}
	}
}
var capas_ope = ["central","a2"];
function checksMaps() {
	//si solo hay en total 4 checkboxes no mostrar los checkboxes
	if($(".maps-checkbox .input-checkbox").length <= 4){
		$(".checkboxes").addClass("d-none");
	}
	
	//en el mapa de OPE en el listado ocultar los ckboxes de corredores
	if(parametrosMapa.mapLayerNameIntro.split(",")[0]=="OPE"){		
		var ckboxes_lista = $(".listadoColaboradores .checkboxes .check-label");
		
		for(var i=0; i<ckboxes_lista.length; i++){
			var ckbox = ckboxes_lista[i];
			var nombre = $(ckbox).text().trim();
			
			if(nombre.split(" ")[0]=="Corredor"){
				$(ckbox).addClass("d-none");
			}
		}
		
		var ckboxes_mapa = $(".map .checkboxes .check-label");
		for(var i=0; i<ckboxes_mapa.length; i++){
			var ckbox = ckboxes_mapa[i];
			var nombre = $(ckbox).text().trim();
			
			if(nombre == "Corredor R4" || nombre == "Corredor R2"){
				$(ckbox).addClass("d-none");
			}
		}
	}
	
	
	$(".maps-checkbox .input-checkbox[type='checkbox']:not('.first-checkbox') ").click(function (e) {
		if($(this).parents(".maps-checkbox").attr("data-type") == "Camino_Santiago") {
			caminos($(this).val());
		} else {
			//detectar de que grupo de checkbox viene el click
			var query_checkboxes = '';
			if($(this).parents(".map").length){
				//si es en el grupo del modo mapa 
				query_checkboxes = '.map .maps-checkbox .input-checkbox';
			}else{
				//si es en el modo lista
				query_checkboxes = '.listadoColaboradores .maps-checkbox .input-checkbox';
			}
			
			//toggle layer 
			var checkboxChange = $(this).val();
			toggleLayer(checkboxChange);
			
			//crear diccionario para relacionar los checkboxes con los elementos de la lista
			var diccionario = {
			"checkbox_value":"data-tipoelemento",
			"Centros_gestion":"CG",
			"Asociacion_victimas":"AV",
			"Centros_ejecutivos":"CE",
			"JEFATURA":"JP",
			"CGT":"CGT",
			"Ayuntamientos_DGT":"AYU",
			"CRC":"CRC",
			"AUTOESCUELA":"AUTOESCUELA",
			"ITV":"ITV",
			"CATV":"CATV",
			"Talleres": "TALLER",
			"OPE_descanso":"OPE_descanso",
			"OPE_informacion":"OPE_informacion",
			"OPE_puertos":"OPE_puertos",
			"Areas_servicio":"Areas_servicio",
			"Salidas":"Salidas",
			"Entradas":"Entradas",
			"Junquera_Total":"Junquera_Total",
			"Irun_Total":"Irun_Total"
			};
			var capa = diccionario[checkboxChange];
			
			//para el mapa de OPE
			if(parametrosMapa.mapLayerNameIntro.split(",")[0]=="OPE"){
				var ck_cent_a2 = $(".map .checkboxes .input-checkbox[value='Corredor_central_A2']");
				var ck_cent = $(".map .checkboxes .input-checkbox[value='Corredor_central']");
				
				
				if($(this)[0].value == "Corredor_central"){
					//Corredor central incorpora trazado R4
					if(ck_cent[0].checked){
						actualizarCapasOPE("Corredor_central",true);
					}else{
						actualizarCapasOPE("Corredor_central",false);
					}
					
				}else if($(this)[0].value == "Corredor_central_A2"){
					//Corredor central A2 incorpora trazado R4 y R2
					if(ck_cent_a2[0].checked){
						actualizarCapasOPE("Corredor_central_A2",true);
					}else{
						actualizarCapasOPE("Corredor_central_A2",false);
					}

				}
				
			}
			
			
			
			//esconder los elementos de las listas que haya, en este caso el sidebar y la lista del modo lista			
			//si hay algun filtro activo de provincias, CCAA, etc hay que tenerlo en cuenta aqui
			if(this.checked){
				//checkbox activado -> se muestra la capa que corresponda
				let cod_ine;
				if($('.custom-select.provinciaMap').length > 1){
					cod_ine = $('.custom-select.provinciaMap').find(":selected")[0].dataset.provid;
				}
				//comprobar aqui si hay un filtro activo y si lo hay esconder las cards que correspondan
				if(cod_ine){					
					//quitar el d-none de los elementos que tengan el mismo codigo INE
					$(".sidebar .accordion .card[data-codine="+cod_ine+"][data-tipoelemento="+capa+"]").removeClass("d-none");
					$(".listadoColaboradores .maps-accordion .accordion .card[data-codine="+cod_ine+"][data-tipoelemento="+capa+"]").removeClass("d-none");
				}else{
					//filtro no activo
					$(".sidebar .accordion .card[data-tipoelemento="+capa+"]").removeClass("d-none");
					$(".listadoColaboradores .accordion .card[data-tipoelemento="+capa+"]").removeClass("d-none");
				}
			}else{
				//checkbox desactivado -> se esconde la capa que correspanda
				$(".sidebar .accordion .card[data-tipoelemento="+capa+"]").addClass("d-none");
				$(".listadoColaboradores .accordion .card[data-tipoelemento="+capa+"]").addClass("d-none");
			}
			
			
			//main check status update
			var main_check = $(query_checkboxes+".first-checkbox");
			
			var restOfChecks = $(query_checkboxes);
			var index = restOfChecks.length;
			//keep the count, +1 if 1 check is ON, -1 if check is OFF 
			var count = 0;
			for (i = 1; i < index; i++) {
				if(restOfChecks[i].checked){
					count = count + 1;
				}else{
					count = count - 1;
				}
			}
			if(count == index-1){
				//they are all ON, put main check ON
				main_check.prop('checked', true);
				main_check.prop("indeterminate", false);
				main_check.removeClass("indeterminate");
			}else if(count == -(index-1)){
				//they are all OFF, put main check OFF
				main_check.prop('checked', false);
				main_check.prop("indeterminate", false);
				main_check.removeClass("indeterminate");
			}else{
				//some are OFF some are ON, put main check NEUTRAL
				main_check.prop("indeterminate", true);
				main_check.addClass("indeterminate");
			}
			
		}
	});
}

function caminos(camino, nombreCamino) {

	// TODO
	/* if (camino == ('CRC') || ('CATV') || ('ITV') || ('AUTOESCUELA') || ('CGT') || ('camaras_web')) {
		if (camino == 'camaras_web') {
			var centro = camino;
			toggleLayer(centro);
		}
		else {
			var checkeds = $(".maps-checkbox input:checked");

			center = centro;

			if (camino.checked == true) {
				// getCenters(centro);
				if (myLongitude && myLatitude) {
					findPointsInRadius(centro, myLongitude, myLatitude, 3000);
					ubicate(myLongitude, myLatitude, "", 100);
				}
			}

			if (!checkeds.length) {
				var infoMapa = $(".map .sidebar");
				let elemAcordionMap = $(".maps-accordion", infoMapa);
				$(".accordion", elemAcordionMap).html("");
				$(infoMapa).removeClass("open");
			}
		}
	} */
		parametroNombre = nombreCamino;
		var tipoCamino = camino.split("_");
		caminoName = camino;
	if (tipoCamino) {
		toggleLayer("Puntos_" + tipoCamino[1]);
		toggleLayer("POI_" + tipoCamino[1]);
		toggleLayer("Traza_" + tipoCamino[1]);
		toggleLayer("Tramos_" + tipoCamino[1]);
		console.log("tipoCamino:" + tipoCamino[1]);
		centerTrackSantiago('Traza_' + tipoCamino[1]);
		
		/* var infoMapa = $(".map .sidebar");
		let elemAcordionMap = $(".maps-accordion", infoMapa);
		$(".accordion", elemAcordionMap).html(""); */
		getStages('POI_' + tipoCamino[1]);
		getStages('Tramos_' + tipoCamino[1]);
	} 
	var checkeds = $(".maps-checkbox input:checked");
	
	if (!checkeds.length) {
		var infoMapa = $(".map .sidebar");
		let elemAcordionMap = $(".maps-accordion", infoMapa);
		$(".accordion", elemAcordionMap).html("");
		$(infoMapa).removeClass("open");
	}
}
function anclaTramoOPuntoPeligroso(e, elem){
	mjeDebug("click en punto o tramo peligroso");
	mjeDebug(elem.attr("data-type"));
	mjeDebug(elem.attr("data-peligrosidad"));
	$(".sidebar.open").animate({
		scrollTop: 0
	}, 20);
	setTimeout(function () {
		var elementToDisplay = $(".card[data-peligrosidad=" + elem.attr("data-peligrosidad") + " ][data-type=" + elem.attr("data-type") + " ]");
		elementToDisplay.children()[0].children[1].className = "collapse show";
		var top = $(".card[data-peligrosidad=" + elem.attr("data-peligrosidad") + " ][data-type=" + elem.attr("data-type") + " ]").offset().top;
		var scroll = top - $(".sidebar.open").offset().top;
		$(".sidebar.open").animate({
			scrollTop: scroll - 80
		}, 2000);
		centerIcoMap(elementToDisplay);
	}, 300);
}

function mainCheck() {
	$(".maps-checkbox .input-checkbox.first-checkbox").change(function () {
		//mainCheck
		var elementSelected = $(this);
		$(this).removeClass("indeterminate");
		//comprobar de que grupo de checkboxes viene el click
		var query_checkboxes = '';
		if($(this).parents(".map").length){
			//si es en el grupo del modo mapa 
			query_checkboxes = '.map .maps-checkbox .input-checkbox';
		}else{
			//si es en el modo lista
			query_checkboxes = '.listadoColaboradores .maps-checkbox .input-checkbox';
		}
		//restChecks
		var restOfChecks = $(query_checkboxes);
		
		if(parametrosMapa.mapLayerNameIntro.split(",")[0]=="OPE"){
			actualizarCapasOPE("main", this.checked);
		}
		
		//esconder los elementos de las listas que haya, en este caso el sidebar y la lista del modo lista
		if(this.checked){
			let cod_ine;
			//comprobar aqui si hay un filtro activo y si lo hay esconder las cards que correspondan
			if($('.custom-select.provinciaMap').length > 1){
				cod_ine = $('.custom-select.provinciaMap').find(":selected")[0].dataset.provid;
			}
			if(cod_ine){	
				//quitar el d-none de los elementos que tengan el mismo codigo INE
				$(".sidebar .accordion .card[data-codine="+cod_ine+"]").removeClass("d-none");
				$(".listadoColaboradores .maps-accordion .accordion .card[data-codine="+cod_ine+"]").removeClass("d-none");
			}else{
				$(".sidebar .accordion .card").removeClass("d-none");
				$(".listadoColaboradores .accordion .card").removeClass("d-none");
			}
		}else{
			$(".sidebar .accordion .card").addClass("d-none");
			$(".listadoColaboradores .accordion .card").addClass("d-none");
		}
		
		
		//if true show all layers
		var index = restOfChecks.length;
		if (elementSelected[0].checked == true) {
			for (i = 1; i < index; i++) {
				//if its uncheck, check & toggle layer
				if(!restOfChecks[i].checked){
					restOfChecks[i].checked = true;
					toggleLayer(restOfChecks[i].value);
				}
				//if its check, do nothing
			}
		}else{
		//if false hide all layer
			for (i = 1; i < index; i++) {
				//if its check, uncheck & toggle layer
				if(restOfChecks[i].checked){
					restOfChecks[i].checked = false;
					toggleLayer(restOfChecks[i].value);
				}
				//if its uncheck, do nothing
			}
		}
	});
}

function displayInfoMap(dataJson, tipoInfo, elementSelected) {
	console.log("dataJson" + dataJson);
	console.log("tipoInfo" + tipoInfo);
	console.log("elementSelected" + elementSelected);
	var elemento_seleccionado = elementSelected;
	if (elementSelected.attributes) {
		var layerSelected = elementSelected.attributes[0].capa;
	}
	if (dataJson) {
		if (tipoInfo == 'combo' || tipoInfo == 'datosPunto') {
			if (tipoInfo == 'datosPunto') {
				//set data variables
				elementSelectedName = elementSelected.attributes[0].NAMEUNIT;
				elementSelectedID = elementSelected.attributes[0].COD_INE;
				elementSelected = $(".custom-select.ccaaMap > option");
				elementSelected.each(function () {
					if (this.getAttribute("data-ccaaid") == elementSelectedID) {
						var name = this.attributes[1].value;
						$(".custom-select.ccaaMap").val(name);
					}
				});
				
				//si esta en modo responsive
				if(getViewport() == 'sm'){
					var cod_ine = elemento_seleccionado.attributes[0].COD_INE;
					var card = $(".listadoColaboradores .accordion .card[data-id="+parseInt(cod_ine)+"_lista"+"]");
					//meter el card dentro del sidebarDetail y mostrarlo
					$(".sidebarDetail .accordion").html("");
					$(".sidebarDetail .titulo .titulo p").html("");
					
					//poner el nombre de la ccaa como titulo
					var titulo = $(".card-header button", card).first().text();
					$(".sidebarDetail .titulo .titulo p").append(titulo);
					
					//meter el card interior dentro del accordion
					var cards_interior = $(".collapse", card).first();
					$(".sidebarDetail .accordion").append(cards_interior.html());
					
					//mostrarlo
					$(".sidebarDetail").addClass("d-block");
					$(".sidebarDetail").addClass("open");
				}else{
					//cerrar todos las cards
					$('.sidebar .accordion .collapse').removeClass("show");
					//poner el scroll arriba del todo para poder calcular correctamente la scroll_distance
					$(".sidebar.open").animate({
						scrollTop: 0
					}, 0);
					var cod_ine = elemento_seleccionado.attributes[0].COD_INE;
					var card = $(".sidebar .accordion .card[data-id="+parseInt(cod_ine)+"]");
					//abrir card
					$(".collapse", card).first().addClass("show");	
					//coords del card
					var card_height = card.offset().top; 
					//distancia que tiene que hacer scroll = coord del card menos el coord del sidebar
					var sidebar_height = $(".sidebar.open").offset().top;
					var scroll_distance = card_height - sidebar_height;
					//se hace el scroll sobre este lugar
					$(".sidebar.open").animate({
						scrollTop: scroll_distance
					}, 2000);
				}
				
			} else {
				elementSelected = $(".custom-select.ccaaMap option:selected");
				elementSelectedName = elementSelected.val();
				elementSelectedID = elementSelected.attr("data-ccaaid");
			}
			
			
		}else if (tipoInfo == 'getStages') {
			console.log("elementSelected" + elementSelected);
			var checkboxSelected = $(".maps-checkbox input[value="+ elementSelected +"]");

			//var n = $("input:checked").length;
			var checkeds = $(".maps-checkbox input:checked");
			var infoMapaSantiago = $(".map .sidebar");
			 
			var stages = [];

			
			// $(".map.santiagoMap .sidebar .title-caminos").html(elementSelected);
			var infomacionAsociada = "";
			var stages = "";

			var stages = dataJson.stages;
			var caminoSelected = $(".checkboxes-caminos input");
			// $(".accordion", infoMapaSantiago).html("");
			
				if (infomacionAsociadaCamino == null || infomacionAsociadaCamino == undefined) {
					$(".sidebar .infoTitulo").text(parametrosMapa.mapLayerNameIntro)
			infomacionAsociadaCamino = '<div class="card ' + elementSelected + '">'
					+ '<div class="card-header" >'
					+ '<h3 class="right-0 title title-maps-traffic">'
					+ '<img class="icon-maps" src="' + baseUrlInterna + 'camino_' + elementSelected.split("_")[1] + '.png" />'
					+ '<button class="btn btn-link text-capitalize" type="button" data-toggle="collapse" data-target="#mapAccordion' + elementSelected + '" aria-expanded="true" aria-controls="mapAccordion' + elementSelected + '"> ' + parametroNombre
					+ '<i class="fas fa-chevron-down" ></i>'
					+ '<i class="fas fa-chevron-up" ></i>'
					+ '</button>'
					+ '</h3>'
					+ '</div>';

}
			// $('.filter .form-group select option[value=' + dataJson.attributes[0].NAMEUNIT + '');
			$(stages).each(function (index) {
				etapaNumStages = stages[index].OBJECTID;
				if (stages[index].Name) {
					etapaNumSplit = stages[index].Name.split(".-");
					etapaName = stages[index].Name;
					etapaCamino = stages[index].Camino;


				} else {
					etapaName = stages[index].ETAPA;
					etapaCamino = stages[index].CAMINO;
					etapaNumSplit = etapaName;
					var intersection = stages[index].INTERSEC;
					var municipio = stages[index].MUNICIPIO;
					var via = stages[index].VIA;

				}
				
				if (!stages[index].INTERSEC) {
					var dataType = "tramo"
				} else {
					var dataType = "poi"
				}

				if (stages[index].Peligrosidad) {
					var peligrosidad = "-peligro";
				} else {
					var peligrosidad = "";
				}

				infomacionAsociada = '<div class="card ' + elementSelected + '" data-type="' + dataType + '" data-peligrosidad="' + stages[index].Peligrosidad + '" data-id="' + etapaNumStages + '" data-label="' + elementSelected.split("_")[1] + '">'
				+ '<div class="card-header">'
				+ '<h3 class="right-0 title title-maps-traffic">';

				if (!stages[index].INTERSEC) {
					infomacionAsociada += '<img class="icon-maps" src="' + baseUrlInterna + 'Tramo' + peligrosidad + '.png" />';

				} else if (stages[index].Peligrosidad) {
					infomacionAsociada += '<img class="icon-maps" src="' + baseUrlInterna + 'camino_peligro.png" />';
				}
				else {
					infomacionAsociada += '<img class="icon-maps" src="' + baseUrlInterna + 'camino_' + elementSelected.split("_")[1] + '-concha.png" />';

				}
				if (etapaName.split(".-")[1]) {
					var nombreEtapa = etapaName.split(".-")[1];

				} else {
					var nombreEtapa = etapaName;
				}

				infomacionAsociada += '<button class="btn btn-link" type="button" data-toggle="collapse" data-target="#collapse' + etapaNumStages + '" aria-expanded="false" aria-controls="collapse' + etapaNumStages + '">' + nombreEtapa
					+ '<i class="fas fa-chevron-down" ></i>'
					+ '<i class="fas fa-chevron-up" ></i>'
					+ '</button>'
					+ '</h3>'
					+ '<div id="collapse' + etapaNumStages + '" class="collapse" aria-labelledby="heading' + etapaNumStages + '" data-parent="#mapAccordion' + elementSelected + '">'
					+ '<div class="card-body bg-traffic">'
					+ '<ul class="ul-maps" data-id="' + etapaNumStages + '">';

				infomacionAsociada += '	<li class="traffic-data">'
					+ '<p class="bold">Nombre: </p>'
					+ '<p class="fs-16">&nbsp' + etapaName + '</p>'
					+ '	<li class="traffic-data">'
					+ '<p class="bold">Camino: </p>'
					+ '<p class="fs-16">&nbsp' + etapaCamino + '</p>'
					+ '	<li class="traffic-data">'
					+ '<p class="bold">Carretera: </p>'
					+ '<p class="fs-16">&nbsp' + via + '</p>'
					+ '	<li class="traffic-data">'
					+ '<p class="bold">Municipio: </p>'
					+ '<p class="fs-16">&nbsp' + municipio + '</p>';
				if (stages[index].INTERSEC) {
					infomacionAsociada += '	<li class="traffic-data">'
						+ '<p class="bold">Intersección: </p>'
						+ '<p class="fs-16">&nbsp' + intersection + '</p>';
				}

				infomacionAsociada += '</li>' + '</li>' + '</li>' + '</li>' + '</li>';

				infomacionAsociada += '</ul>'
					+ '</div>'
					+ '</div>'
					+ '</div>';
				infomacionAsociada += '</ul>'
					+ '</div>'
					+ '</div>'
					+ '</div>';

				str1 = "mapAccordion";
				str2 = elementSelected;
				res = str1.concat(str2);

				$("#mapAccordion").attr("id", "mapAccordion" + str2);

				$("#mapAccordion" + str2, infoMapaSantiago).append(infomacionAsociada);
			});
			$("#mapAccordion" + str2, infoMapaSantiago).addClass("show");
			infomacionAsociadaCamino += '</div>'
				+ '</div>';

			//$(".accordion.etapaPunto").html("");


			$(".titleCamino", infoMapaSantiago).append(infomacionAsociadaCamino);
			if (infoMapaSantiago.hasClass("open")) {
				calculoPosicionBotonesMapa();
			}
			else {
				$(".titleCamino .card" + '.' + elementSelected).remove();
				var infoMapa = $(".map .sidebar");
				let elemAcordionMap = $(".maps-accordion", infoMapa);
				$(".accordion", elemAcordionMap).html("");
				$(infoMapa).removeClass("open");
			}
			infomacionAsociadaCamino = "";
	}
		
		else if (tipoInfo == 'evento') {
			var infoMapa = $(".map .sidebar");
			var correo = "";
			let elemAcordionMap = infoMapa;
			$(".accordion", elemAcordionMap).html("");	// Borramos el contenido que tenga
			var infomacionAsociada = "";
			var informacionAsociadaCombo = "";
			$(infoMapa).addClass("open");
			
			//pintar por plantillas
			let elem =  elementSelected;
			//renderDataMapTemplate(elem, "mapa", "1", "");
			var info_evento = renderDataMapTemplate(elem, "listado", "1", "mapAccordion");
			
			$(".sidebarMap .accordion").append(info_evento);
			//romper el collapse del card del accordion
			$(".sidebarMap .accordion .card button").removeAttr("data-target");
			//meter la info del evento dentro del sidebarDetail 
			var infoCard_evento = $(".sidebarMap .accordion .card .card-body");
			$(".sidebarDetail .accordion").append(infoCard_evento.html());
			$(".sidebarDetail .titulo p").html($(".sidebarMap .accordion .card button").text());	
			$(".sidebarDetail").addClass("d-block");
			$(".sidebarDetail").addClass("open");
		}
	} else if (layerSelected == 'CRC' || layerSelected == 'ITV' || layerSelected == 'CATV' || layerSelected == 'Talleres' || layerSelected == 'Ayuntamientos_DGT' || layerSelected == 'JEFATURA' || layerSelected == 'AUTOESCUELA' || 
			layerSelected == 'Asociacion_victimas' || layerSelected == 'Centros_ejecutivos' || layerSelected == 'Centros_gestion' || 
			layerSelected == 'Camaras_web' || layerSelected == 'Radares_punto' || layerSelected == 'Radares_tramo_punto' || layerSelected == 'Radares_tramo' ||
			layerSelected == 'Tramos_motos_puntos' || layerSelected == 'Tramos_motos_lineas' ||
			layerSelected == 'Rutas_ciclisas_seguras' || layerSelected == 'Rutas_bicicletas') {
		
		var infoMapaCombo = $(".mt-5.list-view.container");

		let elemAcordion = $(".maps-list-out", infoMapaCombo);

		
		$(".accordion", elemAcordion).html("");	// Borramos el contenido que tenga

		let elem =  elementSelected.attributes[elementSelected.attributes.length - 1];
		
		//hacer consulta con el objectID para mostrar la info en el sidebarDetail
		$(".sidebarDetail").addClass("d-block");
		$(".sidebarDetail").addClass("open");
		
		//para el mapa de motos
		if(elem.capa == "Tramos_motos_lineas" || elem.capa == "Tramos_motos_puntos"){
			elem.tipo_elemento = "Tramos_motos_puntos";
		}
		
		//contenido del sidebarDetail
		let query = ".sidebar .accordion .card[data-objectid='"+elem.OBJECTID+"'][data-tipoelemento='"+elem.tipo_elemento+"']";
		let titulo = $( query + " button").first().text();
		//let contenido = $( query + " .row").first();
		
		//buscar el contenido por atributo data-id en el listadoColaboradores
		var card = $(".listadoColaboradores .accordion .card[data-id="+elem.id+"]").first();
		var contenido = $(".card-body .row", card).first().html();
		
		//revertimos los estilos del listado
		contenido = $(contenido).removeClass("col-md-9 col-md-6 col-md-2");
		$(contenido).children().children().removeClass("col-md-9 col-md-6 col-md-2");
		
		$(".sidebarDetail .titulo p").html(titulo);
		$(".sidebarDetail .accordion").html(contenido);
		
		//poner icono Seleccionado
		removeAllSelectedIcons();
		selectIconFromLayer(elem.capa,elem.OBJECTID);
		
		
	} else if (elementSelected.attributes[0].capa.includes("Tramos_") || elementSelected.attributes[0].capa.includes("Puntos_")|| elementSelected.attributes[0].capa.includes("POI_")) {
		//Si camino de santiago
		dataJson = elementSelected;
		var camino = elementSelected.attributes[0].capa.split("_")[1];
		var idPuntoTramo;
		var esTipoPOI;
		elem = infoMapa;
		$.each(dataJson.attributes,function(key,value){
			if(this.capa != "Traza_" + camino){
				esTipoPOI = this.capa.includes("POI"); 
				idPuntoTramo = this.OBJECTID;
				if(esTipoPOI){
					return false;	//break;
				}
			}
		});
		//$(".accordion", elem).html("");	// Borramos el contenido que tenga
		var infomacionAsociada = "";
		$(".share", elem).hide();
		if (dataJson.attributes.length == 1) {
			var etapa = dataJson.attributes[0].Name;

		} else {
			for (var i = 0; i < dataJson.attributes.length; i++) {
				if (dataJson.attributes[i].Name) {
					var etapa = dataJson.attributes[i].Name;
				}
			}
		}
		// $('.filter .form-group select option[value=' + dataJson.attributes[0].NAMEUNIT + '');
		var infoMapaSantiago = $(".map.santiagoMap .sidebar");

		$(".collapse.show").removeClass("show");

		$(".sidebar.open").animate({
			scrollTop: 0
		}, 1);
		var jsons = dataJson.attributes.length;
		for (var i = 0; i < jsons; i++) {
			if (dataJson.attributes[i].MUNICIPIO) {
				var municipio = dataJson.attributes[i].MUNICIPIO;
				var provincia = dataJson.attributes[i].PROVINCIA;
				var via = dataJson.attributes[i].VIA;
			}
		}
		if (typeof municipio !== 'undefined') {
			infomacionAsociada += '	<li class="traffic-data">'
				+ '<p class="bold">Municipio: </p>'
				+ '<p class="fs-16">&nbsp' + municipio + '</p></li>'
				+ '	<li class="traffic-data">'
				+ '<p class="bold">Provincia: </p>'
				+ '<p class="fs-16">&nbsp' + provincia + '</p></li>'
				+ '	<li class="traffic-data">'
				+ '<p class="bold">Carretera: </p>'
				+ '<p class="fs-16">&nbsp' + via + '</p></li>';
		}
		/* 
						infomacionAsociada += '</ul>'
							+ '</div>'
							+ '</div>'; */

		var etapaCompleta = etapa;
		var cardToDisplay = $(".card[data-id='" + idPuntoTramo + "'][data-type='" + (esTipoPOI ? "poi" : "tramo") + "']");
		$(".collapse",cardToDisplay).addClass("show");

		if (cardToDisplay == null) {
			cardToDisplay = $('.collapse .card-body .traffic-data p.fs-16:contains(' + etapaCompleta + ')');
		}
		$(".accordion").addClass("show");

		var top = $(".card-header .collapse.show").offset().top;
		var scroll = top - $(".sidebar.open").offset().top;
		$(".sidebar.open").animate({
			scrollTop: scroll - 130
		}, 2000);
	} else if(layerSelected == 'DataJSON'){
		if(parametrosMapa.mapLayer == "Desplazamientos_clic"){
			if($(".sidebarDetail").hasClass("open")){	// Damos tiempo a que se ejecuten las animaciones
				$(".sidebarDetail").removeClass("d-block").removeClass("open");
				setTimeout(function(){
					$(".sidebarDetail").addClass("d-block").addClass("open");
				}, 500);
			} else {	// En el caso de no estar abierto no aumentamos la espera
				$(".sidebarDetail").addClass("d-block").addClass("open");
			}
			
			jQuery.each(jsonCGT, function(i, val) {
				if(val.CGT == elementSelected.attributes[0].CGT){
					$(".sidebarDetail .titulo p").html(val.tituloDatosAcordeon);
					var acordeon = $(".contenedorMapas .map .sidebarDetail .accordion");
					acordeon.html("");
					jQuery.each(val.datos, function(i, elem) {
						template = listadoDesplazamientosPlantilla;
						var x = template.replace(/{{templ_id}}/ig, val.id);
						x = x.replace(/{{templ_centro}}/ig, val.centro);
						x = x.replace(/{{templ_tipo_elemento}}/ig, "Datos desplazamiento CGT");
						x = x.replace(/{{templ_parent}}/ig, "#" + acordeon.attr("id"));
						x = x.replace(/{{templ_iterate}}/ig, "_" + i);
						x = x.replace(/{{templ_titulo}}/ig, elem.titulo);
						x = x.replace(/{{templ_descripcion}}/ig, elem.descripcion);
						$(".contenedorMapas .map .sidebarDetail .accordion").append(x);
					});
					return false;
				}
			});
		}
//		$(".sidebarDetail").addClass("d-block").addClass("open");
	}
}

function tipoDocumento(documento){
	var tipo = "";
	if(allowedImgExtensions.exec(documento.toLowerCase())){
		tipo = "imagen";
	} else if(allowedAudioExtensions.exec(documento.toLowerCase())){
		tipo = "audio";
	} else if(allowedFileExtensions.exec(documento.toLowerCase())){
		tipo = "fichero";
	} else if(documento == ""){
		tipo = "actividad";
	} else{
		tipo = "video";
	}
    return tipo;
}

function renderDataMapTemplate(elem, formato, index, idParent){
	if(elem.capa == null){
		if(elem.tipo_elemento){
			elem.capa = colaboradoresTipoElemento[elem.tipo_elemento].capa;
		}else if(elem.Shape__Length){
			if(!elem.Ruta){
				elem.capa = 'Tramos_motos_puntos';
			}
		}else{
			//return "";
		}
	}

	
	var imageSrc = baseUrlInterna + elem.capa + ".svg";
	var imageSrcListado = baseUrlInterna + elem.capa + "-pin.svg";
	var centro = elem.capa;
	var titulo;
	var template;
	
	if(centro == 'CRC'){
		titulo = "Centro de reconocimiento";
	} else if(centro == 'JEFATURA'){
		titulo  = "Jefatura";
	} else if(centro == 'Talleres'){
		titulo  = "Taller";
	} else if(centro == 'Camaras_web'){
		titulo = "Cámara";
	} else if(centro == 'Radares_punto'){
		titulo = "Radar";
	} else if(centro == 'Radares_tramo' || centro == 'Radares_tramo_punto'){
		titulo = "Radar tramo";
	} else if(centro == 'Tramos_motos_puntos' || centro == 'Tramos_motos_lineas'){
		titulo = "Tramo riesgo motoristas";
	} else if(centro == 'Rutas_ciclisas_seguras'){
		titulo = "Rutas ciclistas seguras";
	} else if(centro == 'Rutas_bicicletas'){
		titulo = "Rutas ciclistas protegidas";
	} else if(centro == 'Centros_ejecutivos'){
		titulo = "Centros ejecutivos";
	} else if(centro == 'Centros_gestion'){
		titulo = "Centros de gestión";
	}else if(centro == 'Asociacion_victimas'){
		titulo = "Asociación de víctimas";
	}else if(centro == 'Ayuntamientos_DGT'){
		titulo = "Ayuntamientos";
	}else if(centro == 'EVENTO'){
		titulo = elem.titulo;
	}else{
		titulo = elem.nombre;
	}
	

	
	
	
	
	
	if (centro == 'Camaras_web' || centro == 'Radares_punto' || centro== 'Radares_tramo' || centro == 'Radares_tramo_punto' || centro == 'Tramos_motos_lineas' || 
			centro == 'Rutas_bicicletas' || centro == 'Rutas_ciclisas_seguras' || centro == 'Rutas_ciclisas_seguras' || centro == 'Rutas_bicicletas' || centro=='Tramos_motos_puntos') {
		
		//selecciona plantilla
		if(centro == 'Tramos_motos_puntos'){
			template = listadoMotosPlantilla;
			elem.tipo_elemento = centro;
		}else{
			template = movilidadPlantilla;
		}
		
		//esto es del template de movilidadPlantilla tendra ciertas variables iguales a la otra plantilla
		var x = template.replace(/{{templ_OBJECTID}}/ig, elem.OBJECTID);
		x = x.replace(/{{templ_codigo_centro}}/ig, elem.codigo_centro);
		x = x.replace(/{{templ_codigo}}/ig, elem.codigo);
		x = x.replace(/{{templ_id}}/ig, elem.id);
		x = x.replace(/{{templ_fid}}/ig, elem.FID);
		x = x.replace(/{{templ_cod_ine}}/ig, elem.cod_ine);
		x = x.replace(/{{templ_fecha}}/ig, elem.fecha);
		x = x.replace(/{{templ_lat}}/ig, elem.latitud);
		x = x.replace(/{{templ_long}}/ig, elem.longitud);
		x = x.replace(/{{templ_imageSrc}}/ig, imageSrc);
		x = x.replace(/{{templ_centro}}/ig, titulo);
		x = x.replace(/{{templ_carretera}}/ig, elem.carretera);
		x = x.replace(/{{templ_display_distancia}}/ig, elem.distancia != null && elem.distancia.toString().trim() != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_distancia}}/ig, elem.distancia);
		x = x.replace(/{{templ_display_periodo}}/ig, elem.periodo != null && elem.periodo.trim() != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_periodo}}/ig, elem.periodo);
		x = x.replace(/{{templ_PKI_texto}}/ig, "Punto kilométrico" + (elem.pk_inicio != null && elem.pk_inicio.toString().trim() != "" ? ' inicio':''));
		x = x.replace(/{{templ_display_PK}}/ig, elem.pk != null && elem.pk.toString().trim() != "" ? 'flex;':elem.pk_inicio != null && elem.pk_inicio.toString().trim() != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_PKI}}/ig, elem.pk != null ? (elem.pk).toString().replaceAll(".",",") : elem.pk_inicio != null ? (elem.pk_inicio).toString().replaceAll(".",",") : "");
		x = x.replace(/{{templ_display_PKF}}/ig, elem.pk_fin != null && elem.pk_fin.toString().trim() != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_PKF}}/ig, elem.pk_fin != null ? (elem.pk_fin).toString().replaceAll(".",",") : "");
		
		x = x.replace(/{{templ_display_limite_gen}}/ig, elem.limite_generico != null && elem.limite_generico.toString().trim() != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_limite_gen}}/ig, elem.limite_generico + " km/h");
		x = x.replace(/{{templ_display_limite}}/ig, elem.limite_velocidad != null && elem.limite_velocidad.toString().trim() != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_limite}}/ig, elem.limite_velocidad + " km/h");
		x = x.replace(/{{templ_display_horario}}/ig, elem.horario != null && elem.horario.trim() != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_horario}}/ig, elem.horario);
		
		if( elem.cod_ine!= null && elem.cod_ine.toString().trim() != "" ){
			var provinciaMapa = (elem.cod_ine.toString().length < 2  ? "0" : "" ) + elem.cod_ine; 
			x = x.replace(/{{templ_display_provincia}}/ig, 'flex;');
			x = x.replace(/{{templ_provincia}}/ig, provinciasId[provinciaMapa]["data-nameProv"]);
			x = x.replace(/{{templ_display_comunidad}}/ig, 'flex;');
			x = x.replace(/{{templ_comunidad}}/ig, provinciasId[provinciaMapa]["data-nameCCAA"]);
		}
		x = x.replace(/{{templ_display_provincia}}/ig, elem.provincia != null && elem.provincia.toString().trim() != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_provincia}}/ig, elem.provincia);
		x = x.replace(/{{templ_display_comunidad}}/ig, elem.comunidad != null && elem.comunidad.trim() != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_comunidad}}/ig, elem.comunidad);
		x = x.replace(/{{templ_display_sentido}}/ig, elem.sentido != null && elem.sentido.trim() != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_sentido}}/ig, elem.sentido);
		x = x.replace(/{{templ_display_victimas}}/ig, elem.victimas != null && elem.victimas.toString().trim() != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_victimas}}/ig, elem.victimas);
		x = x.replace(/{{templ_display_img_camara}}/ig, elem.imagen != null && elem.imagen.trim() != "" && elem.imagen != undefined ? 'flex;':'none;');
		x = x.replace(/{{templ_img_camara}}/ig, elem.imagen + "?" + new Date().getTime());
		
		
		if(centro == 'Tramos_motos_puntos'){
			//rellenar datos del mapa de motos
			x = x.replace(/{{templ_nombre}}/ig, elem.carretera);
			x = x.replace(/{{templ_iterate}}/ig, "TramoMoto"+ index);
			x = x.replace(/{{templ_parent}}/ig, "#"+idParent);
			x = x.replace(/{{templ_tipo_elemento}}/ig, elem.tipo_elemento);
			//x = x.replace(/{{}}/ig, );
		}
		
	} else if (parametrosMapa.mapLayerNameIntro.split(",")[0] == "OPE") {
		template = listadoPuntoOPE;
		//Para el mapa de OPE
		var x = template.replace(/{{templ_OBJECTID}}/ig, elem.OBJECTID);
		x = x.replace(/{{templ_lat}}/ig, elem.Latitud);
		x = x.replace(/{{templ_long}}/ig, elem.Longitud);
		x = x.replace(/{{templ_id}}/ig, index);
		x = x.replace(/{{templ_iterate}}/ig, index);
		x = x.replace(/{{templ_parent}}/ig, "#"+idParent);
		x = x.replace(/{{templ_nombre}}/ig, elem.Area);
		x = x.replace(/{{templ_provincia}}/ig, elem.Provincia);
		
		x = x.replace(/{{templ_display_municipio}}/ig, 'none;');
		x = x.replace(/{{templ_display_comunidad}}/ig, 'none;');
		if(!elem.Tipo){
			//es un puerto
			x = x.replace(/{{templ_imageSrc}}/ig, baseUrlInterna + "OPE_puertos" + "-pin.svg");
			x = x.replace(/{{templ_centro}}/ig, "");
			x = x.replace(/{{templ_direccion}}/ig, elem.Dirección);
			x = x.replace(/{{templ_telefono}}/ig, elem.Teléfono);
			x = x.replace(/{{templ_display_web}}/ig, elem.web != null && elem.web.trim() != "" ? 'flex;':'none;');
			x = x.replace(/{{templ_web}}/ig, elem.web != null && elem.web.includes("http") ? elem.web : "http://" + elem.web);
			x = x.replace(/{{templ_tipo_elemento}}/ig, "OPE_puertos");
			
			x = x.replace(/{{templ_display_PK}}/ig, 'none;');
			x = x.replace(/{{templ_display_extra2}}/ig, 'none;');
			x = x.replace(/{{templ_display_extra1}}/ig, 'none;');
			x = x.replace(/{{templ_display_horario}}/ig, 'none;');
			x = x.replace(/{{templ_display_carretera}}/ig, 'none;');
		}else{				
			x = x.replace(/{{templ_centro}}/ig, elem.Tipo);
			x = x.replace(/{{templ_PK}}/ig, elem.PK);
			x = x.replace(/{{templ_carretera}}/ig, elem.Carretera);
			x = x.replace(/{{templ_horario_titulo}}/ig, "Horario de atención: ");
			x = x.replace(/{{templ_horario_texto}}/ig, elem.Horario_Atencion);
			x = x.replace(/{{templ_horario2_titulo}}/ig, "Periodo de funcionamiento: ");
			x = x.replace(/{{templ_horario2_texto}}/ig, elem.Periodo__Funcionamiento);
			
			x = x.replace(/{{templ_display_direccion}}/ig, 'none;');
			x = x.replace(/{{templ_display_telefono}}/ig, 'none;');
			x = x.replace(/{{templ_display_web}}/ig, 'none;');
			if(elem.Tipo == "Punto Información"){
				x = x.replace(/{{templ_imageSrc}}/ig, baseUrlInterna + "OPE_informacion" + "-pin.svg");
				x = x.replace(/{{templ_extra1_text}}/ig, "Capacidad");
				x = x.replace(/{{templ_extra1}}/ig, elem.Capacidad);
				x = x.replace(/{{templ_extra2_text}}/ig, "Servicios ofrecidos");
				x = x.replace(/{{templ_extra2}}/ig, elem.Servicios__Ofrecidos);
				x = x.replace(/{{templ_tipo_elemento}}/ig, "OPE_informacion");
				
				x = x.replace(/{{templ_display_telefono}}/ig, 'none;');
				x = x.replace(/{{templ_display_web}}/ig, 'none;');
			}else{
				//es un punto de descanso
				x = x.replace(/{{templ_imageSrc}}/ig, baseUrlInterna + "OPE_descanso" + "-pin.svg");
				x = x.replace(/{{templ_tipo_elemento}}/ig, "OPE_descanso");
				
				x = x.replace(/{{templ_display_extra2}}/ig, 'none;');
				x = x.replace(/{{templ_display_extra1}}/ig, 'none;');
			}
		}
	}else if (parametrosMapa.mapLayerNameIntro.split(",")[0] == "OPP"){
		template = listadoPuntoOPP;
		//Para el mapa de OPP
		var x = template.replace(/{{templ_OBJECTID}}/ig, elem.OBJECTID);
		x = x.replace(/{{templ_lat}}/ig, elem.Latitud);
		x = x.replace(/{{templ_long}}/ig, elem.Longitud);
		x = x.replace(/{{templ_id}}/ig, index);
		x = x.replace(/{{templ_iterate}}/ig, index);
		x = x.replace(/{{templ_parent}}/ig, "#"+idParent);
		x = x.replace(/{{templ_titulo2}}/ig, "DIRECCIÓN");
		x = x.replace(/{{templ_titulo3}}/ig, "HORARIO");
		//"Areas_servicio,Salidas,Entradas,Junquera_Total,Irun_Total"
		if(elem.Población){
			//area de servicio
			x = x.replace(/{{templ_titulo1}}/ig, "CENTRO");
			x = x.replace(/{{templ_imageSrc}}/ig, baseUrlInterna + "Areas_servicio" + "-pin.svg");
			x = x.replace(/{{templ_centro}}/ig, "Area de Servicio");
			x = x.replace(/{{templ_nombre}}/ig, elem.Nombre);
			x = x.replace(/{{templ_telefono}}/ig, elem.Teléfono);
			x = x.replace(/{{templ_web}}/ig, elem.Web);
			x = x.replace(/{{templ_extra1_text}}/ig, "Respostaje");
			x = x.replace(/{{templ_extra1}}/ig, elem.Repostaje);
			x = x.replace(/{{templ_extra2_text}}/ig, "Restaurante");
			x = x.replace(/{{templ_extra2}}/ig, elem.Restauran_);
			x = x.replace(/{{templ_direccion}}/ig, elem.Población);
			x = x.replace(/{{templ_horario_texto}}/ig, elem.Horario);
			x = x.replace(/{{templ_tipo_elemento}}/ig, "Areas_servicio");
		}else if(elem.Descripcio){
			//entrada
			x = x.replace(/{{templ_titulo1}}/ig, "Entrada");
			x = x.replace(/{{templ_imageSrc}}/ig, baseUrlInterna + "Entradas" + "-pin.svg");
			x = x.replace(/{{templ_centro}}/ig, "Entrada");
			x = x.replace(/{{templ_nombre}}/ig, elem.Nombre);
			x = x.replace(/{{templ_extra1_text}}/ig, "Vía");
			x = x.replace(/{{templ_extra1}}/ig, elem.Via);
			x = x.replace(/{{templ_extra2_text}}/ig, "Provincia");
			x = x.replace(/{{templ_extra2}}/ig, elem.Provincia);
			x = x.replace(/{{templ_extra3_text}}/ig, "CCAA");
			x = x.replace(/{{templ_extra3}}/ig, elem.CCAA);
			x = x.replace(/{{templ_display_extra3}}/ig, "flex;");
			var enlace = "https://www.visitportugal.com/es/sobre-portugal/info-util";
			x = x.replace(/{{templ_display_extra4}}/ig, "flex;");
			x = x.replace(/{{templ_extra4}}/ig, "Antes de viajar a Portugal, <a href="+enlace+">consulta información relativa a normas de tráfico, peajes y más</a>.");
			x = x.replace(/{{templ_tipo_elemento}}/ig, "Entradas");
			
			x = x.replace(/{{templ_display_direccion}}/ig, 'none;');
			x = x.replace(/{{templ_display_horario}}/ig, 'none;');
			x = x.replace(/{{templ_display_telefono}}/ig, 'none;');
			x = x.replace(/{{templ_display_web}}/ig, 'none;');
			x = x.replace(/{{templ_display_direccion}}/ig, 'none;');
		}else if(elem.Shape__Length){
			//carretera
			x = x.replace(/{{templ_titulo1}}/ig, "Carretera");
			x = x.replace(/{{templ_centro}}/ig, "Ruta");
			x = x.replace(/{{templ_nombre}}/ig, elem.Ruta);
			x = x.replace(/{{templ_extra1_text}}/ig, "Distancia");
			x = x.replace(/{{templ_extra1}}/ig, elem.Distancia);
			x = x.replace(/{{templ_extra2_text}}/ig, "Tiempo");
			x = x.replace(/{{templ_extra2}}/ig, elem.Tiempo);
			if(elem.Distabcia){
				x = x.replace(/{{templ_tipo_elemento}}/ig, "Irun_Total");
				x = x.replace(/{{templ_imageSrc}}/ig, baseUrlInterna + "Irun_Total" + "-pin.svg");
			}else{
				x = x.replace(/{{templ_tipo_elemento}}/ig, "Junquera_Total");
				x = x.replace(/{{templ_imageSrc}}/ig, baseUrlInterna + "Junquera_Total" + "-pin.svg");
			}
			
			
			x = x.replace(/{{templ_display_direccion}}/ig, 'none;');
			x = x.replace(/{{templ_display_horario}}/ig, 'none;');
			x = x.replace(/{{templ_display_telefono}}/ig, 'none;');
			x = x.replace(/{{templ_display_web}}/ig, 'none;');
			x = x.replace(/{{templ_display_direccion}}/ig, 'none;');
		}else{
			//salida
			x = x.replace(/{{templ_titulo1}}/ig, "Salida");
			x = x.replace(/{{templ_imageSrc}}/ig, baseUrlInterna + "Salidas" + "-pin.svg");
			x = x.replace(/{{templ_centro}}/ig, "Salida");
			x = x.replace(/{{templ_nombre}}/ig, elem.Nombre);
			x = x.replace(/{{templ_extra1_text}}/ig, "Via");
			x = x.replace(/{{templ_extra1}}/ig, elem.Via);
			x = x.replace(/{{templ_extra2_text}}/ig, "Provincia");
			x = x.replace(/{{templ_extra2}}/ig, elem.Provincia);
			x = x.replace(/{{templ_extra3_text}}/ig, "CCAA");
			x = x.replace(/{{templ_extra3}}/ig, elem.CCAA);
			x = x.replace(/{{templ_display_extra3}}/ig, "flex;");
			x = x.replace(/{{templ_tipo_elemento}}/ig, "Salidas");
			
			x = x.replace(/{{templ_display_direccion}}/ig, 'none;');
			x = x.replace(/{{templ_display_horario}}/ig, 'none;');
			x = x.replace(/{{templ_display_telefono}}/ig, 'none;');
			x = x.replace(/{{templ_display_web}}/ig, 'none;');
			x = x.replace(/{{templ_display_direccion}}/ig, 'none;');
		}
		x = x.replace(/{{templ_display_extra3}}/ig, "none;");
		x = x.replace(/{{templ_display_extra4}}/ig, "none;");
	}else if (centro == 'Corredor_central' || centro == 'Corredor_central_A2' || centro== 'Corredor_mediterraneo' || centro == 'Corredor_R2' || centro== 'Corredor_R4' || centro== 'Corredor_via_plata') {	
			/* estas capas no tienen datos */			
	} else if(parametrosMapa.tipoElementoCustomPoints == "stars" || parametrosMapa.tipoElementoCustomPoints == "stars-historico" || parametrosMapa.tipoElementoCustomPoints == "new-stars-historico" || parametrosMapa.tipoElementoCustomPoints == "new-stars"){
		template = listadoPuntoStars;
		//para el mapa de Stars
		if(parametrosMapa.tipoElementoCustomPoints == "stars" || parametrosMapa.tipoElementoCustomPoints == "stars-historico"){
			var x = template.replace(/{{templ_OBJECTID}}/ig, elem.OBJECTID);
			x = x.replace(/{{templ_lat}}/ig, elem.latitud);
			x = x.replace(/{{templ_long}}/ig, elem.longitud);
			x = x.replace(/{{templ_id}}/ig, index);
			x = x.replace(/{{templ_iterate}}/ig, index);
			x = x.replace(/{{templ_parent}}/ig, "#"+idParent);
			x = x.replace(/{{templ_nombre}}/ig, elem.nombre);
			x = x.replace(/{{templ_provincia}}/ig, elem.provincia);
			x = x.replace(/{{templ_direccion}}/ig, elem.direccion);
			x = x.replace(/{{templ_comunidad}}/ig, elem.comunidad);
			x = x.replace(/{{templ_cod_ine}}/ig, elem.cod_ine_prov.trim());
			x = x.replace(/{{templ_tipo_elemento}}/ig, elem.tipo_elemento);
			x = x.replace(/{{templ_imageSrc}}/ig, baseUrlInterna + "listado-" + elem.ico2);
			x = x.replace(/{{templ_municipio}}/ig, elem.municipio);
			
			//buscar por codigo de centro en el otro json la puntuacion y medalla
			elem.puntos = responseJson[elem.codigo_centro].puntuacion;
			elem.medalla = responseJson[elem.codigo_centro].medalla;
			
			let valorMedalla;
			if(responseJson[elem.codigo_centro] != undefined){
				valorMedalla = responseJson[elem.codigo_centro].medalla != '' ? responseJson[elem.codigo_centro].medalla : '4';
			}
			
			if(elem.puntos == undefined || elem.puntos == ""){
				x = x.replace(/{{templ_display_puntos}}/ig, "none");
			}
			
			x = x.replace(/{{templ_puntos}}/ig, elem.puntos);
			x = x.replace(/{{templ_medalla}}/ig, '<span class="mapa medalla medalla-' + valorMedalla + '">' + medallas[valorMedalla] + '</span>');
		}else{
			var x = template.replace(/{{templ_OBJECTID}}/ig, elem.id);
			x = x.replace(/{{templ_lat}}/ig, elem.latitud);
			x = x.replace(/{{templ_long}}/ig, elem.longitud);
			x = x.replace(/{{templ_id}}/ig, index);
			x = x.replace(/{{templ_iterate}}/ig, index);
			x = x.replace(/{{templ_parent}}/ig, "#"+idParent);
			x = x.replace(/{{templ_nombre}}/ig, elem.nombre_centro);
			x = x.replace(/{{templ_municipio}}/ig, elem.poblacion);
			var provincia = provinciasId[elem.cod_ine_prov]
			x = x.replace(/{{templ_provincia}}/ig, provincia["data-nameProv"]);
			x = x.replace(/{{templ_direccion}}/ig, elem.direccion +" , "+ elem.numero);
			var comunidad = provinciasId[elem.cod_ine_prov];
			x = x.replace(/{{templ_comunidad}}/ig, comunidad["data-nameCCAA"]);
			x = x.replace(/{{templ_cod_ine}}/ig, elem.cod_ine_prov.trim());
			x = x.replace(/{{templ_tipo_elemento}}/ig, "stars");
			var ico_sidebar = elem.ico.split("/");
			ico_sidebar = ico_sidebar[ico_sidebar.length-1];
			x = x.replace(/{{templ_imageSrc}}/ig, baseUrlInterna + "listado-" + ico_sidebar);
			
			//buscar por codigo de centro en el otro json la puntuacion y medalla
			elem.puntos = elem.l1;
			elem.medalla = elem.l2;
			
			let valorMedalla;
			if(elem.codigo_centro != undefined){
				valorMedalla = elem.l2 != '' ? elem.l2 : '4';
			}
			
			if(elem.puntos == undefined || elem.puntos == ""){
				x = x.replace(/{{templ_display_puntos}}/ig, "none");
			}
			
			x = x.replace(/{{templ_puntos}}/ig, elem.puntos);
			x = x.replace(/{{templ_medalla}}/ig, '<span class="mapa medalla medalla-' + valorMedalla + '">' + medallas[valorMedalla] + '</span>');
		}	
	}else if(parametrosMapa.tipoElementoCustomPoints == "safetytunes" || parametrosMapa.tipoElementoCustomPoints == "escaperoom" || parametrosMapa.tipoElementoCustomPoints == "caminoescolar" || parametrosMapa.tipoElementoCustomPoints == "juegoserpiente"){
		template = listadoPuntoSafetytunes;
		var x = template.replace(/{{templ_OBJECTID}}/ig, elem.id);
		x = x.replace(/{{templ_lat}}/ig, elem.latitud);
		x = x.replace(/{{templ_long}}/ig, elem.longitud);
		x = x.replace(/{{templ_id}}/ig, index);
		x = x.replace(/{{templ_iterate}}/ig, index);
		x = x.replace(/{{templ_parent}}/ig, "#"+idParent);
		x = x.replace(/{{templ_cod_ine}}/ig, elem.cod_ine_prov.trim());
		x = x.replace(/{{templ_tipo_elemento}}/ig, elem.tipo_elemento);
		x = x.replace(/{{templ_imageSrc}}/ig, baseUrlInterna + "listado-" + elem.ico2);
		
		x = x.replace(/{{templ_nombre}}/ig, elem.nombre);
		
		x = x.replace(/{{templ_display_img}}/ig, elem.extra1 != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_img}}/ig, elem.extra1);
		x = x.replace(/{{templ_direccion}}/ig, elem.direccion);
		x = x.replace(/{{templ_display_direccion}}/ig, elem.direccion != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_direccion}}/ig, elem.direccion);
		x = x.replace(/{{templ_municipio}}/ig, elem.municipio);
		x = x.replace(/{{templ_provincia}}/ig, elem.provincia);
		x = x.replace(/{{templ_comunidad}}/ig, elem.comunidad);
		x = x.replace(/{{templ_display_correo}}/ig, elem.email != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_correo}}/ig, elem.email);
		
		x = x.replace(/{{templ_display_documentos}}/ig, elem.documento.length != "" ? 'flex;':'none;');
		x = x.replace(/{{templ_display_actualizacion}}/ig, elem.info != "" ? 'flex;':'none;');
		
		if(parametrosMapa.tipoElementoCustomPoints == "safetytunes"){
			x = x.replace(/{{templ_recursos}}/ig, "RECURSOS");
		}else{
			//x = x.replace(/{{templ_recursos}}/ig, "ACTIVIDADES");
			x = x.replace(/{{templ_recursos}}/ig, "");
			x = x.replace(/{{templ_display_doc}}/ig, "none;");
		}
		
		var html_docs = "";
		var documentos = elem.documento;
		for(var i=0; i<documentos.length; i++){
			var documento = documentos[i];

			var icono = "";
			var tipo = tipoDocumento(documento.url);
			var data = ["",""];
			var download = "";
			var href = "";
			var clase = "";
			var audio = "";
			var id_audio = "";
			switch(tipo){
				case "imagen":
				case "video":
					icono = "icon-dgt-eye";
					data[0] = "modal";
					data[1] = "#genericModal";
					break;
				case "audio":
					icono = "icon-dgt-speaker-line";
					clase = "audio";
					id_audio = "span_audio_";
					audio = ""+
						"<audio id='"+elem.id+"_"+i+"'>"+
						"<source src='"+documento.url+"' type='audio/mpeg'>"+
						" Tú navegador no soporta el tag de audio HTML5"+
						"</audio>";
					break;
				case "fichero":
					icono = "icon-dgt-download_n";
					var doc = documento.url.split("/");
					download = "download='"+doc[doc.length-1]+"'";
					href = documento.url;
					break;
				case "actividad":
					icono = "icono-dgt-sin-documento";
					clase = "actividad-mapa";
					break;
			}
			
			//antiguo
			/*var templ_doc = ""+
				"<a class='mostrarImg documento row ml-1 fs-16 "+clase+"' href='"+href+"' "+download+" data-toggle='"+data[0]+"' data-target='"+data[1]+"' style='color:#333'>"+
					"<span class='iconoTipo mr-1 "+icono+"' style='margin-top: 1px;'></span>"+
					"<span data-img='"+documento.url+"' id='"+id_audio+elem.id+"_"+i+"'>"+
					documento.titulo+audio+
				"</a>";*/
				
			var templ_doc = ""+
				"<a class='mostrarImg documento row ml-1 fs-16 "+clase+"' href='"+href+"' "+download+" data-toggle='"+data[0]+"' data-target='"+data[1]+"' style='color:#333'>"+
					"<span class='iconoTipo mr-1 "+icono+"' style='margin-top: 1px;'></span>"+
					"<span class='titulo' data-img='"+documento.url+"' id='"+id_audio+elem.id+"_"+i+"'>"+documento.titulo+audio+"</span><br>"+
					"<span class='fecha'>("+elem.info+")</span>"+
				"</a>";
			if(tipoDocumento(documento.url)=="actividad"){
				var templ_doc = ""+
				"<li class='"+clase+"' "+download+" style=''>"+
					"<span class='iconoTipo mr-1 "+icono+"' style='margin-top: 1px;'></span>"+
					"<span data-img='"+documento.url+"' id='"+id_audio+elem.id+"_"+i+"'>"+
						documento.titulo.split("|")[0]+
					"</span><br>"+
					"<span style='color:#666'>"+documento.titulo.split("|")[1]+"</span>"+
				"</li>";
			}
			
			html_docs += templ_doc; 
		}
		x = x.replace(/{{templ_documentos}}/ig, html_docs);
		x = x.replace(/{{templ_actualizacion}}/ig, elem.info);
	}else {
		/*vienen con cadena valor null, las pasamos a autentico null para que condiciones de abajo lo pillen y no lo muestren*/
		if(elem.fax==="null"){elem.fax=null;}
		if(elem.telefono==="null"){elem.telefono=null;}
		if(elem.web==="null"){elem.web=null;}
		if(elem.movil==="null"){elem.movil=null;}
		//usar plantilla listadoColaboradores
		template = listadoColaboradoresPlantilla;
		if(centro=='Asociacion_victimas') {
			template = listadoColaboradoresPlantillaAV;
		}
		var x = template.replace(/{{templ_iterate}}/ig, elem.tipo_elemento + index);
		console.log("nombre:"+elem.nombre+" descripcion:" + elem.descripcion + " elem.codpostal:" + elem.codigo_postal + " cod_ine:" +  elem.cod_ine); 
		
		
		
		
		x = x.replace(/{{templ_parent}}/ig, "#"+idParent);
        x = x.replace(/{{templ_OBJECTID}}/ig, elem.OBJECTID);
        x = x.replace(/{{templ_id}}/ig, elem.id);
        x = x.replace(/{{templ_codigo_centro}}/ig, elem.codigo_centro);
        x = x.replace(/{{templ_tipo_elemento}}/ig, elem.tipo_elemento);
        x = x.replace(/{{templ_cod_ine}}/ig, elem.cod_ine);//COD_INE
        x = x.replace(/{{templ_lat}}/ig, elem.latitud);
		x = x.replace(/{{templ_long}}/ig, elem.longitud);

        x = x.replace(/{{templ_imageSrc}}/ig, imageSrcListado);
		//x = x.replace(/{{templ_imageSrc}}/ig, formato == 'mapa' ? imageSrc : imageSrcListado);
        if(centro == 'JEFATURA' || centro == 'Centros_gestion' || centro == 'Ayuntamientos_DGT' || centro == 'Centros_ejecutivos'){
        	if(formato == "mapa"){
        		x = x.replace(/{{templ_centro}}/ig, titulo);
        	} else {
        		x = x.replace(/{{templ_centro}}/ig, "");
        		if(centro == 'JEFATURA' ){
					if(elem.codigo_centro.length < 3) elem.codigo_centro = "0" + elem.codigo_centro;
	        		let elemJefatura = jefaturasExtra[elem.codigo_centro]; // Eliminarlo cuando exista solo el nuevo listado
					
					
		            x = x.replace(/{{templ_display_otros}}/ig, elemJefatura.examenes_titulo != null && elemJefatura.examenes_titulo.trim() != "" ? 'flex;':'none;');	/* para poder mostrar otros en caso del listado de Jefaturas*/
        		}
        	}
        } else { /* centro == 'Asociacion_victimas' */
        	//x = x.replace(/{{templ_centro}}/ig, titulo);
        	//x = x.replace(/{{templ_centro}}/ig, centro.toLowerCase());
        }
		if (centro == 'ITV'){
        	x = x.replace(/{{templ_nombre}}/ig, elem.nombre + " - " + elem.municipio);
        } else {
			x = x.replace(/{{templ_nombre}}/ig, elem.nombre);
		}
        
        x = x.replace(/{{templ_display_descripcion}}/ig, elem.descripcion != null && elem.descripcion.trim() != "" ? 'flex;':'none;');
       	x = x.replace(/{{templ_descripcion}}/ig, elem.descripcion);
       	x = x.replace(/{{templ_display_ambito}}/ig, elem.ambito!= null && elem.ambito.trim() != "" ? 'flex;':'none;');
       	x = x.replace(/{{templ_ambito}}/ig, elem.ambito);
       	x = x.replace(/{{templ_display_direccion}}/ig, elem.direccion != null && elem.direccion.trim() != "" ? 'flex;':'none;');
       	x = x.replace(/{{templ_direccion}}/ig, elem.direccion);
        x = x.replace(/{{templ_display_municipio}}/ig, elem.municipio != null && elem.municipio.trim() != "" ? 'flex;':'none;');
        x = x.replace(/{{templ_municipio}}/ig, elem.municipio);
        x = x.replace(/{{templ_display_provincia}}/ig, elem.provincia != null && elem.provincia.toString().trim() != "" ? 'flex;':'none;');
        x = x.replace(/{{templ_provincia}}/ig, elem.provincia);
        x = x.replace(/{{templ_display_comunidad}}/ig, elem.comunidad != null && elem.comunidad.trim() != "" ? 'flex;':'none;');
        x = x.replace(/{{templ_comunidad}}/ig, elem.comunidad);
        x = x.replace(/{{templ_display_codigo_postal}}/ig, elem.codigo_postal != null && elem.codigo_postal.toString().trim() != "" ? 'flex;':'none;');
        x = x.replace(/{{templ_codigo_postal}}/ig, elem.codigo_postal != null ? elem.codigo_postal : '');
        x = x.replace(/{{templ_display_telefono}}/ig, elem.telefono != null && elem.telefono.toString().trim() != "" ? 'flex;':'none;');
        x = x.replace(/{{templ_telefono}}/ig, elem.telefono);
        x = x.replace(/{{templ_display_movil}}/ig, elem.movil != null && elem.movil.toString().trim() != "" ? 'flex;':'none;');
        x = x.replace(/{{templ_movil}}/ig, elem.movil);
        x = x.replace(/{{templ_display_fax}}/ig, elem.fax != null && elem.fax.toString().trim() != "" ? 'flex;':'none;');
        x = x.replace(/{{templ_fax}}/ig, elem.fax);
        x = x.replace(/{{templ_display_correo}}/ig, elem.email != null && elem.email.trim() != "" ? 'flex;':'none;');
        x = x.replace(/{{templ_correo}}/ig, elem.email);
		if(centro == 'JEFATURA' ) {	/* Eliminar If cuando ya este eliminada la web en el origen de los datos*/
        	x = x.replace(/{{templ_display_web}}/ig, 'none;');
		}																																					  											   
        x = x.replace(/{{templ_display_web}}/ig, elem.web != null && elem.web.trim() != "" ? 'flex;':'none;');
        x = x.replace(/{{templ_web}}/ig, elem.web != null && elem.web.includes("http") ? elem.web : "http://" + elem.web);
        x = x.replace(/{{templ_display_extra2}}/ig, elem.extra2 != null && elem.extra2.trim() != "" ? 'flex;':'none;');
        x = x.replace(/{{templ_extra2_text}}/ig, "Oficina de registro");
        x = x.replace(/{{templ_extra2}}/ig, elem.extra2);
        if (centro == 'ITV'){
        	x = x.replace(/{{templ_display_info}}/ig, 'none;');
        }
        
        
        if (centro == 'JEFATURA'){
            let elemJefatura = jefaturasExtra[elem.codigo_centro];
            if(elemJefatura != undefined){
            	if(elemJefatura.horario_texto == null || elemJefatura.horario_texto.trim() == ""){
            		x = x.replace(/{{templ_display_horario}}/ig, 'none;');
            	} else {
            		x = x.replace(/{{templ_display_horario}}/ig, formato == "mapa" ? 'contents;' : 'flex;');
            	}
            	
            	x = x.replace(/{{templ_display_horario_titulo}}/ig, elemJefatura.horario_titulo != null && elemJefatura.horario_titulo.trim() != "" ? 'inline-flex;':'none;');
	            x = x.replace(/{{templ_horario_titulo}}/ig, elemJefatura.horario_titulo);
	            x = x.replace(/{{templ_display_horario_texto}}/ig, elemJefatura.horario_texto != null && elemJefatura.horario_texto.trim() != "" ? 'inline-flex;':'none;');
	            x = x.replace(/{{templ_horario_texto}}/ig, elemJefatura.horario_texto);
	            x = x.replace(/{{templ_display_horario2_titulo}}/ig, elemJefatura.horario2_titulo != null && elemJefatura.horario2_titulo.trim() != "" ? 'inline-flex;':'none;');
	            x = x.replace(/{{templ_horario2_titulo}}/ig, elemJefatura.horario2_titulo);
	            x = x.replace(/{{templ_display_horario2_texto}}/ig, elemJefatura.horario2_texto != null && elemJefatura.horario2_texto.trim() != "" ? 'inline-flex;':'none;');
	            x = x.replace(/{{templ_horario2_texto}}/ig, elemJefatura.horario2_texto);
	            x = x.replace(/{{templ_display_texto_extra}}/ig, elemJefatura.texto_extra != null && elemJefatura.texto_extra.trim() != "" ? 'flex;':'none;');
	            x = x.replace(/{{templ_texto_extra}}/ig, elemJefatura.texto_extra);
	            x = x.replace(/{{templ_display_examenes_titulo}}/ig, elemJefatura.examenes_titulo != null && elemJefatura.examenes_titulo.trim() != "" ? 'flex;':'none;');
	            x = x.replace(/{{templ_examenes_titulo}}/ig, elemJefatura.examenes_titulo);
	            x = x.replace(/{{templ_display_examenes_texto}}/ig, elemJefatura.examenes_texto != null && elemJefatura.examenes_texto.trim() != "" ? 'flex;':'none;');
	            x = x.replace(/{{templ_examenes_texto}}/ig, elemJefatura.examenes_texto);
	            x = x.replace(/{{templ_display_extra1}}/ig, elem.extra1 != null && elem.extra1.trim() != "" ? 'flex;':'none;');
	            x = x.replace(/{{templ_extra1_text}}/ig, "Código DIR3");
	            x = x.replace(/{{templ_extra1}}/ig, elem.extra1.split("|")[0]);
	            x = x.replace(/{{templ_display_extra_pipe}}/ig, elem.extra1 != null && elem.extra1.trim() && elem.extra1.split("|").length > 1 ? 'flex;':'none;');
	            x = x.replace(/{{templ_extra_pipe_text}}/ig, "Oficina de registro");
	            x = x.replace(/{{templ_extra_pipe}}/ig, elem.extra1.split("|")[1]);
            }
        } else if(centro=='Asociacion_victimas') {
			x = x.replace(/{{templ_extra1_text}}/ig, "Ámbito de actuación");
			x = x.replace("Otros:", "Descripción:");
		}else if(centro == 'AUTOESCUELA'){
			x = x.replace(/{{templ_display_horario}}/ig, 'none;');
        	x = x.replace(/{{templ_display_examenes_titulo}}/ig, 'none;');
            x = x.replace(/{{templ_display_examenes_texto}}/ig, 'none;');
            x = x.replace(/{{templ_display_extra1}}/ig, 'none;');
			x = x.replace(/{{templ_display_extra_pipe}}/ig, elem.extra1 != null && elem.extra1.trim() && elem.extra1.split("|").length > 1 ? 'flex;':'none;');
			if(	elem.info!==null && typeof elem.info!== 'undefined'){
				let info = elem.info.split(";");
				//separamos la info 
				let cod_seccion = info[0];
				let cursos = info.splice(1,5);
				let permisos = info.splice(6,info.length);
			
				//bucle para seleccionar los permisos
				let nombres_permisos = [];
				for(let i = 0; i < permisos.length; i++){
					let permiso = permisos[i].split(":");
					if(permiso[1]=="x"){
						nombres_permisos.push(permiso[0].split("_")[2].toUpperCase());
					}
				}
				
				//bucle para seleccionar los cursos
				let nombres_cursos = [];
				for(let i = 0; i < cursos.length; i++){
					let curso = cursos[i].split(":");
					if(curso[1]=="s"){
						nombres_cursos.push(curso[0].split("_")[2]);
					}
				}
				
				//ordeno los permisos y cursos alfabeticamente
				nombres_permisos = nombres_permisos.sort();
				nombres_cursos = nombres_cursos.sort();
				
				//codigo de seccion
				let num_cod = cod_seccion.split(":")[1];
				
				//muestro todos los datos juntos
				let todo = [].concat(num_cod).concat(nombres_cursos).concat(nombres_permisos);
				
				let infoAutoescuela_permisos = '<li class="traffic-data" style="display:flex;"> <p class="bold">Permisos:&nbsp;</p><p class="fs-16 per">';
				let infoAutoescuela_cursos = '<li class="traffic-data" style="display:flex;"> <p class="bold">Cursos:&nbsp;</p><p class="fs-16 cur">';
				let infoAutoescuelaEND = '</p></li>';				
				
				//creo todos los li de permisos
				let datasLI_permisos = '';
				for(let i=0; i<nombres_permisos.length-1; i++){
					datasLI_permisos += nombres_permisos[i]+", ";
				}
				datasLI_permisos += nombres_permisos[nombres_permisos.length-1];
				
				//creo todos los li de cursos
				let datasLI_cursos = '';
				for(let i=0; i<nombres_cursos.length-1; i++){
					datasLI_cursos += nombres_cursos[i]+", ";
				}
				datasLI_cursos += nombres_cursos[nombres_cursos.length-1];
				
				$(".per").html(datasLI_permisos);
				$(".cur").html(datasLI_cursos);
				
				let lista_permisos = infoAutoescuela_permisos + datasLI_permisos + infoAutoescuelaEND;
				let lista_permisos_cursos = infoAutoescuela_permisos + datasLI_permisos + infoAutoescuela_cursos + datasLI_cursos + infoAutoescuelaEND;
				
				x = x.replace(/{{templ_display_info}}/ig, elem.info != null && elem.info.toString().trim() != "" ? 'flex;':'none;');
				x = x.replace(/{{templ_info}}/ig, nombres_cursos.length == 0 ? lista_permisos : lista_permisos_cursos);
			}
        }else if(centro=="EVENTO"){
			//Centro, Direccion y Municipio se pintan por defecto
			
			//horario
			let fecha = $(".fecha")[0];
			let hora = $(".hora")[0];
			x = x.replace(/{{templ_display_horario}}/ig, elem.horario != null && elem.horario.descripcion.trim() != "" ? 'flex;':'none;');
			x = x.replace(/{{templ_horario}}/ig, elem.horario);
			x = x.replace(/{{templ_display_horario_titulo}}/ig, 'none;');
			x = x.replace(/{{templ_display_horario_texto}}/ig, fecha != null && fecha.innerText.trim() != "" ? 'inline-flex;':'none;');
			x = x.replace(/{{templ_horario_texto}}/ig, fecha.innerText + " de " + hora.innerText);
			x = x.replace(/{{templ_display_horario2_titulo}}/ig, 'none;');
			x = x.replace(/{{templ_centro}}/ig, elem.titulo);
			x = x.replace(/{{templ_horario2_titulo}}/ig, elem.horario2_titulo);
			x = x.replace(/{{templ_display_horario2_texto}}/ig, 'none;');
		    x = x.replace(/{{templ_horario2_texto}}/ig, elem.horario2_texto);
			x = x.replace(/{{templ_display_texto_extra}}/ig, elem.texto_extra != null && elemJefatura.texto_extra.trim() != "" ? 'flex;':'none;');
			x = x.replace(/{{templ_texto_extra}}/ig, elem.texto_extra);
			x = x.replace(/{{templ_horario_titulo}}/ig, '');
			//web
			x = x.replace(/{{templ_display_web}}/ig, elem.web != null && elem.web.trim() != "" ? 'flex;':'none;');
			x = x.replace(/{{templ_web}}/ig, elem.web != null && elem.web.includes("http") ? elem.web : "http://" + elem.web);
			//formato
			x = x.replace(/{{templ_display_extra1}}/ig, elem.formato != null && elem.formato.trim() != "" ? 'flex;':'none;');
			x = x.replace(/{{templ_extra1_text}}/ig, "Formato");
			x = x.replace(/{{templ_extra1}}/ig, elem.formato);
			
		}
		
        x = x.replace(/{{templ_display_info}}/ig, elem.info != null && elem.info.toString().trim() != "" ? 'flex;':'none;');
        x = x.replace(/{{templ_info}}/ig, elem.info);
        
		x = x.replace(/{{templ_centro}}/ig, "");
        x = x.replace(/{{templ_display_horario}}/ig, 'none;');
    	x = x.replace(/{{templ_display_examenes_titulo}}/ig, 'none;');
        x = x.replace(/{{templ_display_examenes_texto}}/ig, 'none;');
        x = x.replace(/{{templ_display_otros}}/ig, 'none;');
		
        x = x.replace(/{{templ_extra1_text}}/ig, "Código DIR3");
        x = x.replace(/{{templ_display_extra1}}/ig, elem.extra1 != null && elem.extra1.trim() != "" ? 'flex;':'none;');
        x = x.replace(/{{templ_extra1}}/ig, elem.extra1);
        x = x.replace(/{{templ_display_extra_pipe}}/ig, elem.extra1 != null && elem.extra1.trim() && elem.extra1.split("|").length > 1 ? 'flex;':'none;');
	}
    
	if(formato == "mapa"){
		$(".accordion", $(".map .sidebar")).html("").append(x);
	} else {
		// no pintamos ya que se esta generando todos los contenidos
	}
	return x;
}

function removeRepeated(array) {
	//if(array[0].cod_ine){
	//}
	
	//hacemos un hashmap para quitar los objetos repetidos
	var city_map = new Map();
	
	for(var i=0; i<array.length; i++){
		var item = array[i];
		
		if(!city_map.has( item.city.trim() )){
			city_map.set(item.city.trim(), item);
		}
	}
	
	//pasamos el mapa con objetos unicos de vuelta a un array
	array = [];
	var i = 0; 
	for (const [key, value] of city_map.entries()) {
		array[i] = value;
		i++;
	}
	
	return array;
}

function setTowns(towns) {
    let comboTowns = $(".form-group .custom-select.towns");
    comboTowns.html("");
    var infoMapa = $(".map .sidebar");
    
    towns = removeRepeated(towns);
	
    let nlargo = towns.length;
	console.log("longitud de ciudades:"+nlargo);
	
    if (towns.length > 2) {
        comboTowns.append('<option> Cualquier población</option>');

        towns.sort(function (a, b) {
            return a.city.localeCompare(b.city); // Ordenar alfabéticamente
        });
		console.log("towns: ");
		console.log(towns);
        towns.forEach(function (town) {
            if (town.cod_ine) {
                comboTowns.append('<option value="' + town.city.replaceAll("'","")+ '" cod_ine="' + town.cod_ine + '">' + town.city.replaceAll("'","") + '</option>');
            } else {
                comboTowns.append('<option value="' + town.city.replaceAll("'","") + '">' + town.city.replaceAll("'","") + '</option>');
            }
        });
    }
}



function setRoads(roads) {
	let comboRoads = $(".form-group .custom-select.roads");
	var infoMapa = $(".map .sidebar");
	// infoMapa.html("");
	//infoMapa.removeClass("open");
	comboRoads.html("");
	comboRoads.append('<option> Cualquier carretera</option>');
	roads.forEach(function (road) {
		if(!comboRoads.html().includes(road.road))
			comboRoads.append(`<option value="${road.road}">${road.road}</option>`);
	});

}

function setRoadsProvincia(roads_array) {
	//setea todas las carreteras de una provincia con multiples capas activadas
	let comboRoads = $(".form-group .custom-select.roads");
	var infoMapa = $(".map .sidebar");
	// infoMapa.html("");
	//infoMapa.removeClass("open");
	comboRoads.html("");
	comboRoads.append('<option> Cualquier carretera</option>');
	roads_array.forEach(function (roads) {
		roads.forEach(function (road){
			//la incluye si no esta repetida
			if(!comboRoads.html().includes(road.road))
			comboRoads.append(`<option value="${road.road}">${road.road}</option>`);
		});
	});

}

function loadMapInfo(infoMapa, tipo, dataJson, tipoInfo) {
	var provincia = "";
	let elem = $(".complejo", infoMapa);
	//$(".complejo", infoMapa).removeClass("d-none");
	
	if (tipoInfo == 'datosPunto') {
		/*if(getViewport() == "sm" || getViewport() == "xs"){
			goToAnchor($(".sidebar"));
		}*/
		if (dataJson.attributes) {
			
			//$(infoMapa).addClass("open");
			//$(".sidebarDetail").addClass("open");
			displayInfoMap(responseJson, "datosPunto", dataJson);
			calculoPosicionBotonesMapa();

			
		}
	} else if (tipoInfo == 'getStages') {
		if (dataJson.stages) {
			if($("body").hasClass("caminoDeSantiago")){ // TODO: if temporal hasta que se estabilice el funcionamientos de los distintos mapas
				$(infoMapa).addClass("open");
				console.log('json Stages' + dataJson.stages);
				var elementSelected = caminoName;
				displayInfoMap(dataJson, 'getStages', elementSelected);
			} else {	// TODO: if temporal hasta que se estabilice el funcionamientos de los distintos mapas
				console.log('json Stages modo listado ' + dataJson.stages.length);
				var listado = "";
				
				/*BEGIN BLOCK*/
				
				//Este bloque esta comentado porque ahora el html se tiene que generar de manera 
				//dinamica desde el json.
				
				/*
				//ordena alfabeticamente
				dataJson.stages.sort(function(a, b){
					if(a.nombre){
						return a.nombre.localeCompare(b.nombre, 'es', { sensitivity: 'base' });
					}
				});
				
				dataJson.stages.forEach(function( elem, index){
					listado += renderDataMapTemplate(elem, "listado", index, $(".accordion.dataMap .accordion").attr("id"));	//Pintado por Plantillas
				});
				if(listado != ""){
					//modo mapa
					let map_id = $(".accordion.dataMap .accordion").attr('id');
					let listado_sidebar = replaceAll(listado, map_id, map_id + '_sidebar');
					$(".sidebar.open .accordion").append(listado_sidebar);
					
					//cambios para adaptar listado a sidebar
					$(".sidebar .card-header button").removeAttr("data-toggle");
					$(".sidebar .accordion .collapse").removeAttr("id");
					
					//modo listado
					listado = listado.replace(/{{templ_col_9}}/ig, 'col-md-9');
					listado = listado.replace(/{{templ_col_6}}/ig, 'col-md-6');
					listado = listado.replace(/{{templ_col_2}}/ig, 'col-md-2');
					$(".accordion.dataMap .accordion").append(listado);
					
					//quitamos los collapse del modo mapa para que no vaya lento en los mapas que cargan muchos datos
					if($(".accordion_ccaa").length == 0){
						//si no es el mapa de estrategias y planes
						$(".map .card .collapse").remove();
					}
				}
				*/
				
				/*END BLOCK*/
			}
		}
	}
}
function loadAllStages(dataJson){
	/*
		Carga todos los stages de un mapa para tenerlos en el sidebar y en el listado sirve para mapas que no necesitan filtros
		por provincia o municipio, ej: mapa de corredores
	*/
	//si el mapa no es de stars o corredores salir
	var mapa = parametrosMapa.mapLayerNameIntro.split(",")[0];
	//if(!(mapa == "Stars" || mapa == "OPE")){ este if es el viejo creo que "Stars" ya no hace falta
	if(!(mapa == "motos" || mapa == "OPE" || mapa == "OPP")){
		return;
	}
	/*dataJson.stages.sort(function(a, b){
		if(a.nombre){
			return a.nombre.localeCompare(b.nombre, 'es', { sensitivity: 'base' });
		}
	});*/
	var listado = "";
	dataJson.stages.forEach(function( elem, index){
		listado += renderDataMapTemplate(elem, "listado", index, $(".accordion.dataMap .accordion").attr("id"));	//Pintado por Plantillas
	});
	
	if(listado != ""){
		//modo mapa
		let map_id = $(".accordion.dataMap .accordion").attr('id');
		let listado_sidebar = replaceAll(listado, map_id, map_id + '_sidebar');
		$(".sidebar.open .accordion").append(listado_sidebar);
		
		//cambios para adaptar listado a sidebar
		$(".sidebar .card-header button").removeAttr("data-toggle");
		$(".sidebar .accordion .collapse").removeAttr("id");
		
		//modo listado
		listado = listado.replace(/{{templ_col_9}}/ig, 'col-md-9');
		listado = listado.replace(/{{templ_col_6}}/ig, 'col-md-6');
		listado = listado.replace(/{{templ_col_2}}/ig, 'col-md-2');
		$(".accordion.dataMap .accordion").append(listado);
		
		//quitamos los collapse del modo mapa para que no vaya lento en los mapas que cargan muchos datos
		if($(".accordion_ccaa").length == 0){
			//si no es el mapa de estrategias y planes
			$(".map .card .collapse").remove();
		}
	}
	
}
// codigo externo
function getIframe() {
	return $("iframe.mapa")[0].contentWindow;//document.getElementsByTagName("iframe")[0].contentWindow;
}

//variables globales
//variable globales para el mapa de crc combo de municipios
var get_cities_counter = 0;
var crc_cities = [];

//variable global para mejorar el rendimiento de la pagina
//el objetivo de esta variable es generar el html de forma dinamica en vez de esconder el html mediante estilos
var json_stages;
var stages_caller;
var stages_counter = 0;

function listener(e) {
	var respuesta = JSON.parse(e.data.replaceAll("\t", ""));
	var infoMapa = $(".map .sidebar");
	var comboDisplay = $('#comboProvincias');
	if (respuesta.type == 'buscador') {
		console.log(respuesta.data);
	}

	if (!respuesta.error) {
		if (respuesta.type == "mapa_cargado") {
//			mjeDebug("Iniciando mapas");
			$(".modal-backdrop-map").css("height",$(".contenedorMapas").height());
			$(".modal-backdrop-map").addClass("desaparece");
			setTimeout(function() { 
				$(".modal-backdrop-map").removeClass("show desaparece");
			}, 5000); // tiene que estar sincronizato con los tiempos del css
			
			if(parametrosMapa.tipoElementoCustomPoints == "new-stars-historico" && curso_seleccionado != ""){
				$(".listadoColaboradores .table-filter").html("");
				newStarsAJAX(curso_seleccionado);
			}
			
			mapas();
		} else if (respuesta.type == "datosPunto") {
			if(respuesta.attributes[0].capa != 'CGT'){	/* Por el momento no hay capa CGT, por lo que no mostramos nada*/
				if ($(infoMapa).hasClass("open")) {
					//buscar el elemento en el json_stages
					var stages = json_stages.stages;
					var elemento_seleccionado;
					var mapa = parametrosMapa.mapLayerNameIntro.split(",")[0];
					if(mapa=="jefaturas"){
						//en el mapa de jefaturas hay que buscar por OBJECTID y tipoelemento
						for(var i=0; i<stages.length; i++){
							var stage = stages[i]
							if(stage.OBJECTID == respuesta.attributes[0].OBJECTID && stage.tipo_elemento == respuesta.attributes[0].tipo_elemento){
								elemento_seleccionado = stage;
								break;
							}
						}
					}else if(mapa=="OPE"){
						//si es un corredor salir porque no hace falta mostrar info
						if(respuesta.attributes[0].Shape__Length){
							return;
						}
						
						for(var i=0; i<stages.length; i++){
							var stage = stages[i];
							//busca por Area
							if(stage.Area == respuesta.attributes[0].Area){
								elemento_seleccionado = stage;
								break;
							}
						}
					}else if(mapa=="Planes"){
						displayInfoMap(json_stages, "datosPunto", respuesta)
						return;
					}else if(mapa=="motos"){
						//en motos hay que buscar por OBJECTID
						for(var i=0; i<stages.length; i++){
							var stage = stages[i]
							if(stage.OBJECTID == respuesta.attributes[0].OBJECTID){
								elemento_seleccionado = stage;
								break;
							}
						}	
					}else if(mapa=="OPP"){
						if(respuesta.attributes[0].Shape__Length){
							//si es carretera
							elemento_seleccionado = respuesta.attributes[0]
						}else{
							//si es un punto buscar por OBJECTID y tipoelemento
							elemento_seleccionado = respuesta.attributes[0]
							/*for(var i=0; i<stages.length; i++){
								var stage = stages[i]
								if(stage.OBJECTID == respuesta.attributes[0].OBJECTID && stage.tipoelemento == respuesta.attributes[0].tipo_elemento){
									elemento_seleccionado = stage;
									break;
								}
							}*/
						}
					}else{
						//en los mapas que solo tengan 1 capa solo hace falta por id
						var mapa_custom_aceptados = ["stars","stars-historico","new-stars","new-stars-historico","safetytunes","escaperoom","caminoescolar","juegoserpiente"];
						var mapa_custom = parametrosMapa.tipoElementoCustomPoints;
						for(var i=0; i<stages.length; i++){
							var stage = stages[i]
							if(stage.id == respuesta.attributes[0].id){
								elemento_seleccionado = respuesta.attributes[0];
								if(mapa_custom_aceptados.includes(mapa_custom)){
									elemento_seleccionado = stage;
								}
								break;
							}
						}	
					}
					
					var punto = renderDataMapTemplate(elemento_seleccionado, "listado", "1", "mapAccordion");
					//$(".sidebarDetail .accordion").append(punto);
					
					//poner el nombre del card como titulo
					var titulo = $(".card-header button", punto).first().text();
					$(".sidebarDetail .titulo .titulo p").html(titulo);
					
					//meter el card interior dentro del accordion
					var cards_interior = $(".collapse .row", punto).first();
					$(".sidebarDetail .accordion").html(cards_interior.html());
					
					//abrir y mostrar el sidebarDetail
					$(".sidebarDetail").addClass("d-block");
					$(".sidebarDetail").addClass("open");
					/*
					setTimeout(function () {
	
						loadMapInfo(infoMapa, "complejo", respuesta, "datosPunto");
					}, 400);*/
	
				} else {
					loadMapInfo(infoMapa, "complejo", respuesta, "datosPunto");
				}
			}
		} else if (respuesta.type == "getStages") {
			$(".simple", infoMapa).removeClass("d-none");
			$(".complejo", infoMapa).addClass("d-none");
			
			//sacamos la respuesta a la variable global para generar el html dinamicamente
			if(stages_counter == 0){
				json_stages = respuesta;
				stages_counter = stages_counter + 1;
			}
			else if(stages_counter>0){
				//juntamos los resultados
				json_stages.stages = json_stages.stages.concat(respuesta.stages);
				stages_counter = stages_counter + 1;
				console.log(json_stages)
			}
			
			//cuando se han terminado de cargar todos los stages, los metemos en el sidebar/listado
			var mapa = parametrosMapa.mapLayerNameIntro.split(",")[0];
			if(mapa == "OPE" && stages_counter==3){
				//para mapas que tienen "3 capas de stages" y no filtros
				//ej: OPE, OPP
				loadAllStages(json_stages);
			}else if(mapa == "motos" && stages_counter==1){
				//para mapas que solo tienen "1 capa de stages" y no filtros
				//ej: motos
				loadAllStages(json_stages);
			}else if(mapa == "jefaturas" && stages_counter==3){
				//para mapas que tienen "3 capas de stages" y filtros
				//ej: mapa jefaturas
				inicializarDatosMadrid();
			}else if((mapa != "jefaturas" && mapa != "OPE") && stages_counter==1){
				//para mapas que solo tienen "1 capa de stages" y filtros
				//ej: crc, auto
				inicializarDatosMadrid();
			}else if(mapa == "OPP" && stages_counter==5){
				//para mapas que tienen "5 capas de stages" y no filtros
				//ej: opp
				loadAllStages(json_stages);
			}
			
		}
		else if (respuesta.type == "getCities") {
			console.log("respuesta getcities"); //prueba debug
			if (respuesta.cities) {
				setTowns(respuesta.cities);
			}
			
			switch(get_cities_counter){
				case 0:
					//Esto se tiene que ejecutar primero
					
					//guardamos los municipios que tienen crcs
					var city_options = $(".custom-select.towns option");
					for(var i=0; i<city_options.length; i++){
						crc_cities[i] = city_options[i].value;
					}
					crc_cities.shift();
					console.log(crc_cities);
					
					
					centrosCity = $(".form-group .custom-select.provinciaMap option:selected");
					centrosCityProvid = centrosCity[0].attributes["data-provid"].value;
					//sacamos todos los municipios de la provincia
					toggleLayer("Limite_admin_muni");
					
					//si el centroCityProvid tiene solo un digito poner un 0 delante si no el getCities no retorna nada
					if(centrosCityProvid.length == 1){
						centrosCityProvid = "0"+centrosCityProvid;
					}
					getCities("Limite_admin_muni", centrosCityProvid);
					toggleLayer("Limite_admin_muni");
					
					
					get_cities_counter = get_cities_counter + 1; 
					console.log(" pasa por case 0");
					break;
					
				case 1:
					//Esto se tiene que ejecutar segundo

					//eliminamos los municipios que no tienen crc comparando
					city_options = $(".custom-select.towns option");
					var array_debug = [];
					let longitudCityOption=city_options.length; // log ag
					console.log("num ciudades de city options: "+longitudCityOption); // log ag
					for(var i=1; i<city_options.length; i++){
						var city_option = city_options[i];
						var city_name = parseToId(city_option.value);
						var tiene_crc = false;
						array_debug.push(city_name);
						for(var j=0; j<crc_cities.length; j++){
							var crc_city = parseToId(crc_cities[j].trim());
							city_name=city_name.replaceAll(",\-l",""); // le quitamos ,-l municipio
							crc_city=crc_city.replaceAll("l\-",""); // quitamos l- para que coincida autoescuela
							
							if(city_name.includes("ospitalet")){  // pruebas ag
								  console.log("city name:1 "+city_name+" crc city: "+crc_city);
							  }
							
							//si el nombre coincide no quitar opcion
							if(city_name === crc_city){
							//console.log("city name:2 "+city_name); // log ag
								tiene_crc = true;
								break;
							}
						}
						
						//si no tiene crc quitar opcion
						if(!tiene_crc){
							city_option.remove()
						}
					}
					console.log(array_debug);
					console.log(" pasa por case 1 ");
					get_cities_counter = 0;
					break;
				
				default:
					mjeDebug("getCities counter exception");
					
				
			
			}
			

			
		} else if (respuesta.type == "getMultipleSelection") {
			codsINE = respuesta.codsINE;
		}
		else if (respuesta.type == "getRoads") {
			if (respuesta.roads) {
				console.log("llego la respuesta de getRoads");
				roads.push(respuesta.roads); //meto las carreteras en la variable global roads (l. 274)
				console.log(roads);
				setRoads(respuesta.roads);
			}
		}
		else if (respuesta.type == "vacio") {
			mjeDebug("Click Mapa fuera de elemento");
		}
		else if (respuesta.type == "over") {
			mjeDebug("e.data");
		} else {
			var texto = "";
			//		    JSON.parse(e.data)[0].hasOwnProperty("attributes");	para cuando siempre devuelvan en formato  JSON
			if (respuesta.type == "findPoints") {
				var centrosColaboradores = [];
				var infoMapa = $(".map .sidebar");
				var correo = "";
				let elemAcordionMap = $(".maps-accordion", infoMapa);
				$(".accordion", elemAcordionMap).html("");	// Borramos el contenido que tenga
				var infomacionAsociada = "";
				var informacionAsociadaCombo = "";
				if (respuesta.attributes[0].Tipo_de_elemento == 'CRC') {
					var title = "Centro de reconocimiento";
					respuesta.attributes.forEach(function (element) {
						centrosColaboradores.push(element);
					});
					// var centro = respuesta.attributes.Centro_de_reconocimiento;
					var imageSrc = baseUrlInterna + "PinIndividual_CRC.png";
				}
				if (respuesta.attributes[0].Tipo_de_elemento == 'ITV') {
					var title = "ITV";
					respuesta.attributes.forEach(function (element) {
						centrosColaboradores.push(element);
					});
					var imageSrc = baseUrlInterna + "PinIndividual_ITV.png";
				}

				if (respuesta.attributes[0].Tipo_de_elemento == 'CATV') {
					var title = "CATV";
					respuesta.attributes.forEach(function (element) {
						centrosColaboradores.push(element);
					});
					var imageSrc = baseUrlInterna + "PinIndividual_CATV.png";
				}
				if (respuesta.attributes[0].Correo_electrónico != null) {
					correo = respuesta.attributes[0].Correo_electrónico;
				}
				else {
					correo = "";
				}
				centrosColaboradores.forEach(function (element, index) {

					if (element.Tipo_de_elemento == "ITV") {
						var centroR = element.Autoescuela;
					} else {
						var centroR = element.Centro_autorizado_de_Tratamient;
					}
					infomacionAsociada = '<div class="card" data-id="' + index + '">'
						+ '<div class="card-header">'
						+ '<h3 class="right-0 title title-maps-traffic">'
						+ '<img class="icon-maps" src="' + imageSrc + '" />'
						+ '<button class="btn btn-link" type="button" data-toggle="collapse" data-target="#collapse' + index + '" aria-expanded="false" aria-controls="collapse">' + title
						+ '<i class="fas fa-chevron-down" ></i>'
						+ '<i class="fas fa-chevron-up" ></i>'
						+ '</button>'
						+ '</h3>'
						+ '</div>'
						+ '<div id="collapse' + index + '" class="collapse" aria-labelledby="heading1">'
						+ '<div class="card-body bg-traffic">'
						+ '<ul class="ul-maps">';

					infomacionAsociada +=
						'<li class="traffic-data">'
						+ '<p class="bold">Centro: </p>'
						+ '<p class="fs-16">&nbsp' + centroR + '</p>'

						+ '	<li class="traffic-data">'
						+ '<p class="bold">Dirección: </p>'
						+ '<p class="fs-16">&nbsp' + element.Dirección + '</p>'
						+ '	<li class="traffic-data">'
						+ '<p class="bold">Correo: </p>'
						+ '<p class="fs-16">&nbsp' + correo + '</p>'
						+ '<li class="traffic-data">'
						+ '<p class="bold">Municipio : </p>'
						+ '<p class="fs-16">&nbsp' + element.Municipio + '</p>'

						+ '	<li class="traffic-data">'
						+ '<p class="bold">Teléfono: </p>'
						+ '<p class="fs-16">&nbsp' + element.Teléfono_1 + '</p>';
					infomacionAsociada += '	</li>' + '</li>' + '</li>' + '</li>';

					infomacionAsociada += '</ul>'
						+ '</div>'
						+ '</div>'
						+ '</div>';

					$(".accordion", elemAcordionMap).append(infomacionAsociada);
					$(infoMapa).addClass("open");
					$(".buttons-maps").css("right", "440px");
				});
			}
		}
	} else {
		mjeDebug("ERROR: en respuesta del mapa")
	}
}

// funciones externas 
window.addEventListener("message", listener, false);	// Lo sacamos fuera del on ready por problemas de tiempo de carga
$(function () {
	
	$(".custom-select.ccaaMap").change(function () {
		var elementSelected = $(".custom-select.ccaaMap");
		displayInfoMap(responseJson, "combo", elementSelected)
	});
});

function toggleLayer(layer) {
	sendMessageToIframe(["toggleLayer", layer]);
}

function ubicate(lon, lat, url, zoom) {

	//Icono desde url
	var pictureSymbol = {
		type: "picture-marker",  // autocasts as new PictureMarkerSymbol()
		url: url,
		//"http://gis.dgt.es/mapa/iconos/pin-seleccionado.svg",
		//'https://sede-org.dgt.gob.es/sede-estaticos/Galerias/cabecera/logo_2.jpg',
		//http://localhost/dgt/parent/images/cgt_ico.png', //Modificar por la que corresponda
		//'https://vmopencmsdes02.trafico.es/export/sites/web-DGT/.galleries/Images/dgt_ico.png',
		//'https://gis.dgt.es/iisstart.png',
		width: "27px",
		height: "36px"
	};

	var zoomLevel = zoom != undefined ? zoom : 16;
	sendMessageToIframe(["ubicate", lon, lat, zoomLevel, pictureSymbol]);
	//sendMessageToIframe((["ubicar", lon, lat, zoomLevel]); // Parametro simbolo opcional
}

function findPointsInRadius(layer, lon, lat, radius) {
	if (radius != undefined) {
		sendMessageToIframe(["findPoints", layer, lon, lat, radius]);
	} else {
		sendMessageToIframe(["findPoints", layer, lon, lat]);
	}
}

function centerElement(layer, id, zoom) {
	//Circulo relleno
	var markerSymbol = {
		type: "simple-marker",
		color: [225, 0, 0],
		outline: {
			color: [255, 255, 255],
			width: 2
		}
	};

	//Icono desde url
	var pictureSymbol = {
		type: "picture-marker",  // autocasts as new PictureMarkerSymbol()
		url: baseUrlPin + "pin-individual-crc.svg", //Modificar por la que corresponda
		// "http://gis.dgt.es/mapa/iconos/pin-seleccionado.svg",
		//url: 'https://sede-org.dgt.gob.es/sede-estaticos/Galerias/cabecera/logo_2.jpg',
		//http://localhost/dgt/parent/images/cgt_ico.png', //Modificar por la que corresponda
		//'https://vmopencmsdes02.trafico.es/export/sites/web-DGT/.galleries/Images/dgt_ico.png',
		//'https://gis.dgt.es/iisstart.png',
		width: "24px",
		height: "24px"
	};

	var zoomLevel = zoom != undefined ? zoom : 16;
	sendMessageToIframe(["center", layer, id, zoomLevel, pictureSymbol]);
	//sendMessageToIframe(["center", layer, id, zoomLevel]); //simbolo es parámetro opcional
}

function changeBaseMap(layer) {
	sendMessageToIframe(["changeBaseMap", layer]);
}

function loadInitialLayers(layers) {
	sendMessageToIframe(["loadInitialLayers", layers])
}

function setColor(layer, fillColor, lineColor) {
	sendMessageToIframe(["setColor", layer, fillColor, lineColor]);
}

function sendMessageToIframe(message) {
	getIframe().postMessage(message, "*");
}

function changeCenter(location, miliseconds) {
	sendMessageToIframe(["changeCenter", location, miliseconds]);
}

function searchField(layer, field, data, exactMatch) {
	sendMessageToIframe(["searchField", layer, field, data, exactMatch]);
}

function resetFilterLayer(layer) {
	sendMessageToIframe(["resetFilterLayer", layer]);
}

function setHighlightColor(color) {
	sendMessageToIframe(["setHighlightColor", color]);
}

function setActiveItems(layer, items) {
	sendMessageToIframe(["setActiveItems", layer, items]);
}
function setActiveItemsOutline(color, width) {
	sendMessageToIframe(["setActiveItemsOutline", color, width]);
}

function getInfoCamino(x, y, radius) {
	sendMessageToIframe(["getInfoCamino", x, y, radius]);
}

function getRoads(layer, codProvince) {
	console.log("llama a getRoads")
	sendMessageToIframe(["getRoads", layer, codProvince]);
}

function getBikeRoutes(layer, codProvince, road) {
	sendMessageToIframe(["getBikeRoutes", layer, codProvince, road]);
}

function getCities(layer, codProvince) {
	sendMessageToIframe(["getCities", layer, codProvince]);
}

function getCenters(layer, codProvince, city, type) {
	sendMessageToIframe(["getCenters", layer, codProvince, city, type]);
}

function getProvinces(layer) {
	sendMessageToIframe(["getProvinces", layer]);
}

function getStages(layer) {
	sendMessageToIframe(["getStages", layer]);
}

function addPoint(layerTitle, id, x, y, url) {
	var pictureSymbol = {
		type: "picture-marker",  // autocasts as new PictureMarkerSymbol()
		url: url, //Modificar por la que corresponda
		width: "24px",
		height: "24px"
	};
	sendMessageToIframe(["addPoint", layerTitle, id, x, y, pictureSymbol]);
}

function setMultipleSelection(value) {
	sendMessageToIframe(["setMultipleSelection", value]);
}

function getMultipleSelectionIds() {
	sendMessageToIframe(["getMultipleSelectionIds"]);
}

function clearMultipleSelection() {
	sendMessageToIframe(["clearMultipleSelection"]);
}

function setMultipleSelectionColor(value) {
	sendMessageToIframe(["setMultipleSelectionColor", value]);
}

function setMultipleSelectionFill(value) {
	sendMessageToIframe(["setMultipleSelectionFill", value]);
}

function setMultipleSelectionActiveItems(layer, items) {
	sendMessageToIframe(["setMultipleSelectionActiveItems", layer, items]);
}

function centerTrackSantiago(layer){
    sendMessageToIframe(["centerTrackSantiago", layer]);
}
function selectIconFromLayer(layer, objectId) {
    sendMessageToIframe(["selectIconFromLayer", layer, objectId]);
}

function removeAllSelectedIcons() {
    sendMessageToIframe(["removeAllSelectedIcons"]);
}

function sendJsonCGT(layerTitle) {
    sendMessageToIframe(["sendJsonCGT", layerTitle, jsonCGT]);
}

function hideDataFromJson(layerTitle) {     
	sendMessageToIframe(["hideDataFromJson"], layerTitle);
}

function addPointFromJson(json){
	sendMessageToIframe(["addPointFromJson", json]);
}

function centerElementByCodIne(layer, id, zoom) {
    var zoomLevel = zoom != undefined ? zoom : 16;
    sendMessageToIframe(["centerElementByCodIne", layer, id, zoomLevel]);
}