=========
Mapserver
=========

Description
===========

This is an Ansible role for installing mapserver on a Debian server.
It merely installs mapserver and configures supervisor to run it and
listen on port 8081. In order to actually serve stuff, you need to
create a map file, install a web server, and set it to serve a url
from map server. For example, with ``nginx``::

    location /mapserver-historical {
        gzip off;
        fastcgi_pass 127.0.0.1:8081;
        fastcgi_param SCRIPT_FILENAME /usr/lib/cgi-bin/mapserv;
        fastcgi_param QUERY_STRING map=/var/cache/pthelma/mapserver-historical.map&$query_string;
        include fastcgi_params;
      }

Meta
====

Written by Antonis Christofides

| Copyright (C) 2014-2015 TEI of Epirus
| Copyright (C) 2014-2015 Antonis Christofides

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see http://www.gnu.org/licenses/.
