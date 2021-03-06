Core Data Buildpack
===================

> This is still in early stages of development, so proceed with caution when using this in a production application.
Any bug reports, feature requests, or general feedback at this point would be greatly appreciated.

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for generating a REST web service from a Core Data model. It uses [rack-core-data](https://github.com/mattt/rack-core-data). 

Usage
-----

    $ ls
    Example.xcdatamodel

    $ heroku create --stack cedar --buildpack http://github.com/mattt/heroku-buildpack-core-data.git

    $ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom buildpack
    -----> Core Data detected

This buildpack will detect your app if it includes a Core Data model (`.xcdatamodel`) file. Using [rack-core-data](https://github.com/mattt/rack-core-data), a REST web service that communicates with a [Heroku Postgres](https://postgres.heroku.com) dev database is generated according to the attributes and relationships of each entity in the data model:

<table>
  <thead><tr>
    <th>Core Data Model</th>
    <th>API Endpoints</th>
  </tr></thead>
  <tbody><tr>
    <td><img src="http://heroku-mattt.s3.amazonaws.com/core-data-diagram.png"/></td>
    <td><ul>
      <li><tt>GET /artists</tt></li>
      <li><tt>POST /artists</tt></li>
      <li><tt>GET /artists/1</tt></li>
      <li><tt>PUT /artists/1</tt></li>
      <li><tt>DELETE /artists/1</tt></li>
      <li><tt>GET /artists/1/songs</tt></li> 
    </ul></td>
  </tr></tbody>
</table>

---

## Contact

Mattt Thompson

- http://github.com/mattt
- http://twitter.com/mattt
- mattt@heroku.com

## License

Core Data Buildpack is available under the MIT license. See the LICENSE file for more info.
