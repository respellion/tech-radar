# Motivation

At [Respellion](https://respellion.nl), we maintain a [public Tech
Radar](http://respellion.github.io/tech-radar/) to guide our engineering teams
with technology choices in their projects. We use it as a governance tool to reduce the amount of friction when adopting or experimenting with certain technologies. It is based on the [ThoughtWorks Tech Radar](https://www.thoughtworks.com/radar) and the [Zalando Tech Radar](https://github.com/zalando/tech-radar).

This repository contains the code to generate the visualization:
[`radar.js`](/docs/radar.js) (based on [d3.js v4](https://d3js.org)).
Feel free to use and adapt it for your own purposes.

## Usage

1. include `d3.js` and `radar.js`:

```html
<script src="https://d3js.org/d3.v4.min.js"></script>
<script src="https://respellion.github.io/tech-radar/release/radar-1.js"></script>
```

2. insert an empty `svg` tag:

```html
<svg id="radar"></svg>
```

3. configure the radar visualization:

```js
radar_visualization({
  repo_url: "https://github.com/respellion/tech-radar",
  svg_id: "radar",
  width: 1450,
  height: 1000,
  scale: 1.0,
  colors: {
    background: "#fff",
    grid: "#bbb",
    inactive: "#ddd"
  },
  // Some font families might lead to font size issues
  // Arial, Helvetica, or Source Sans Pro seem to work well though
  font_family: "Arial, Helvetica",
  title: "My Radar",
  quadrants: [
    { name: "Bottom Right" },
    { name: "Bottom Left" },
    { name: "Top Left" },
    { name: "Top Right" }
  ],
  rings: [
    { name: "INNER",  color: "#5ba300" },
    { name: "SECOND", color: "#009eb0" },
    { name: "THIRD",  color: "#c7ba00" },
    { name: "OUTER",  color: "#e09b96" }
  ],
  print_layout: true,
  links_in_new_tabs: true,
  entries: [
   {
      label: "Some Entry",
      link: "link to resource",
      moved: -1       // -1 = moved out (triangle pointing down)
                      //  0 = not moved (circle)
                      //  1 = moved in  (triangle pointing up)
                      //  2 = new       (star)
      quadrant: 3,          // 0,1,2,3 (counting clockwise, starting from bottom right)
      ring: 2,              // 0,1,2,3 (starting from inside)

   },
    // ...
  ]
});
```

Entries are positioned automatically so that they don't overlap. The "scale" parameter can help
in adjusting the size of the radar.

As a working example, you can check out `docs/index.html` &mdash; the source of our [public Tech
Radar](http://respellion.github.io/tech-radar/).

## Deployment

Tech Radar is a static page, so it can be deployed using any hosting provider of your choice offering static page hosting.

## Local Development

1. install dependencies with yarn (or npm):

```
yarn 
```

2. start local dev server:

```
yarn start
```

3. your default browser should automatically open and show the url
 
```
http://localhost:3000/
```
