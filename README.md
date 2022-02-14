# parconMagicMirror

/* Magic Mirror Config Sample
 *
 * By Michael Teeuw http://michaelteeuw.nl
 * MIT Licensed.
 *
 * For more information how you can configurate this file
 * See https://github.com/MichMich/MagicMirror#configuration
 *
 */

var config = {
	address: "localhost", // Address to listen on, can be:
	                      // - "localhost", "127.0.0.1", "::1" to listen on loopback interface
	                      // - another specific IPv4/6 to listen on a specific interface
	                      // - "", "0.0.0.0", "::" to listen on any interface
	                      // Default, when address config is left out, is "localhost"
	port: 8080,
	ipWhitelist: ["127.0.0.1", "::ffff:127.0.0.1", "::1"], // Set [] to allow all IP addresses
	                                                       // or add a specific IPv4 of 192.168.1.5 :
	                                                       // ["127.0.0.1", "::ffff:127.0.0.1", "::1", "::ffff:192.168.1.5"],
	                                                       // or IPv4 range of 192.168.3.0 --> 192.168.3.15 use CIDR format :
	                                                       // ["127.0.0.1", "::ffff:127.0.0.1", "::1", "::ffff:192.168.3.0/28"],

	language: "pt-br",
	timeFormat: 24,
	units: "metric",
	// serverOnly:  true/false/"local" ,
			     // local for armv6l processors, default 
			     //   starts serveronly and then starts chrome browser
			     // false, default for all  NON-armv6l devices
			     // true, force serveronly mode, because you want to.. no UI on this device
	
	modules: [
		{
			module: "alert",
		},
		{
			module: "updatenotification",
			position: "top_bar"
		},
		{
			module: "clock",
			position: "top_left"
		},
		{
			module: "calendar",
			header: "Agenda",
			position: "top_left",
			config: {
				calendars: [
					{

						url: 'https://calendar.google.com/calendar/ical/olXXX%40gmail.com/XXX/basic.ics',
						symbol: 'calendar-check',
					auth: {
						user: 'XXX',
						pass: 'XXX',
						method: 'basic'
					}
								

		},
					
					//{
						//symbol: "calendar-check",
						//url: "https://calendar.google.com/calendar/ical/pt.brazilian%23holiday%40group.v.calendar.google.com/public/basic.ics"					}
				],
			}
		},
		{
			module: "compliments",
			position: "lower_third",
			config: {
	compliments: {
		anytime: [
			"Olhe seus compromissos",			
			"Olhe seu e-mail",
			"Beba água",
			"Leia 5 páginas por dia"
		],
		morning: [
			"Bom dia!",
			"Agradeça por mais um dia.",
			""
		],
		afternoon: [
			"Revise suas matérias",
			"Boa Tarde!",
			""
		],
		evening: [
			
			"Boa noite",
			"Já tá na hora de dormir?"
		],
		day_sunny: [
			"Today is a sunny day",
			"Passe protetor"
		],
		rain: [
			"Não esqueça o guarda-chuva, irá chover"
		]

	}
}
		},
		{
			module: "currentweather",
			position: "top_right",
			config: {
				location: "Brasilia",
				locationID: "3469058",  //ID from http://bulk.openweathermap.org/sample/city.list.json.gz; unzip the gz file and find your city
				appid: "70a0f3a0417440e5b484cd1049c1f5d4"
			}
		},
		{
			module: "weatherforecast",
			position: "top_right",
			header: "Previsão do Tempo",
			config: {
				scale:"true",
				colored:"true",
				location: "Brasilia",
				locationID: "3469058",  //ID from http://bulk.openweathermap.org/sample/city.list.json.gz; unzip the gz file and find your city
				appid: "70a0f3a0417440e5b484cd1049c1f5d4"
			}
		},
		{
			module: "newsfeed",
			position: "bottom_bar",
			config: {
				feeds: [
					{
						title: "Correio Braziliense",
						url: //"https://www.theguardian.com/world/brazil/rss"
							"https://www.correiobraziliense.com.br/rss/noticia/brasil/rss.xml"
					},
					{
						title: "New York Times",
						url: "http://www.nytimes.com/services/xml/rss/nyt/HomePage.xml"					
					}

				],
				showSourceTitle: true,
				showPublishDate: true,
				broadcastNewsFeeds: true,
				broadcastNewsUpdates: true
			}
		},
	]

};

/*************** DO NOT EDIT THE LINE BELOW ***************/
if (typeof module !== "undefined") {module.exports = config;}
