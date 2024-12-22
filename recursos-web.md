# Recursos para Pagina web de Dronoz

## FLYSAFE DJI (método-no-seguro)

API de DJI para ver los [lugares seguros](https://fly-safe.dji.com/nfz/nfz-query) para volar. Aqui esta la [API de areas (faltan parámetros)](https://www-api.dji.com/api/geo/areas). Para visualizar un mapa y realizar efectos dentro del mapa, utilizar [Mapas Leaflet](https://react-leaflet.js.org/docs/start-installation/).

Método de uso:

Necesitamos 2 coordenadas, se debe trazar una linea imaginaría entre estos dos puntos, A y B, donde nuestra ubicación debe estar al medio del punto A y B. Ejemplo:

```txt
-36.594788198972246,-72.13382720947267
-36.62372540364225,-72.06893920898439
```

Teniendo las dos coordenadas se agregan como parámetros a la API de DJI. Ejemplo:

```
https://flysafe-api.dji.com/api/qep/geo/feedback/areas/in_rectangle
?ltlat={latitud} // Punto A
&ltlng={longitud} // Punto A
&rblat={latitud} // Punto B
&rblng={longitud} // Punto B
&zones_mode=flysafe_website // Modo de zonas
&drone=dji-mini-2 // Modelo de dron
&level=1,2 // Niveles de zonas (0, 1, 2, 3, 7, 8).
```

Ejemplo de uso:

```shell
curl 'https://flysafe-api.dji.com/api/qep/geo/feedback/areas/in_rectangle?ltlat=-36.71191679507448&ltlng=-73.22490692138673&rblat=-36.82742436651226&rblng=-72.96535491943361&zones_mode=flysafe_website&drone=dji-mavic-3&level=0,1,2,3,7,8'
```

Respuesta:

```json
{
  "code": 0,
  "message": { "chinese": "成功", "english": "OK" },
  "data": {
    "areas": [
      {
        "area_id": 30281370,
        "name": "Carriel Sur Airport",
        "type": 10,
        "shape": 2,
        "lat": -36.771449,
        "lng": -73.061325,
        "radius": 6000,
        "level": 2,
        "begin_at": 0,
        "end_at": 0,
        "country": "CL",
        "city": "",
        "polygon_points": null,
        "color": "#DE4329",
        "url": "",
        "sub_areas": [
          {
            "color": "#DE4329",
            "height": 0,
            "level": 2,
            "lat": -36.772663969877435,
            "lng": -73.06309024758583,
            "radius": 4187,
            "polygon_points": [
              [
                [-73.0888143507, -36.8041905217],
                [-73.0495781206, -36.736592774],
                [-73.037366723, -36.7411426532],
                [-73.0765915382, -36.8087392932],
                [-73.0888143507, -36.8041905217]
              ]
            ],
            "shape": 1
          },
        ],
        "description": "",
        "height": 0,
        "address": "",
        "data_source": 2
      },
    ],
    "country": "CL",
    "lat": -36.7696,
    "lng": -73.095131,
    "radius": 13223
  }
}
```
