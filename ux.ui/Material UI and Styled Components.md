# Material UI & Styled Components

---

### Why use Material UI?

```
npm i @material-ui/core

```

- React UI framework which provides ready-to-use styled components
- Can import grid-based layouts, responsive animations, transitions and depth effects such as lighting and shadows.

---

## What are some other benefits?
* Allows you to build themes relatively quickly with ```@material-ui/system```
    * ⚛️ Access the theme values directly from the component props.
    * 🦋 Encourage UI consistency.
    * 🌈 Write responsive style effortlessly.
    * 💅 Work with the most popular CSS-in-JS solutions.
    * 📦 Less than 4 KB gzipped.
* Has ready-made templates we can use for sign-up and login
* You can also overrride the default styling of Material UI


---

### Basic How-to
Import what you need, create the component, add properties and export it

```javascript=
import AppBar from '@material-ui/core/AppBar'
import Toolbar from '@material-ui/core/Toolbar'
import Typography from '@material-ui/core/Typography'

const NavBar = () => {
    return(
        <div>
        <AppBar position="static">
            <Toolbar>
                <Typography variant="title" color="inherit">
                React & Material-UI Sample Application
                </Typography>
            </Toolbar>
        </AppBar>
        </div>
    )
}

export default NavBar;
```

---

#### Grid
- Grid properties allow customization of size/element type e.g. container, item, lg, md, sm, justify 

```javascript
import { Grid } from "@material-ui/core/Grid";
import Card from "@material-ui/core/Card";
import CardMedia from "@material-ui/core/CardMedia";
import { posts } from "./posts";

function Posts(props) {
  return (
    <div>
      <Grid container spacing={40} justify="center">
        {posts.map(post => (
          <Grid item key={post.title}>
            <Card>
                <CardMedia
                  component="img"
                  height="140"
                  image={post.image}
                  title="Contemplative Reptile"
                />
              <CardActions>
                <Button size="small" color="primary">
                  Share
                </Button>
                <Button size="small" color="primary">
                  Learn More
                </Button>
              </CardActions>
            </Card>
          </Grid>
        ))}
      </Grid>
    </div>
  );
}
```

---

### Customising Material UI components

import makeStyles and use it as CSS. Add the className to the component

```javascript=
import { makeStyles } from '@material-ui/core/styles';

const useStyles = makeStyles({
  media: {
    width: '100px',
    height: '75px',
  }
});

function ImageCard() {
  const classes = useStyles();
  
  return (
 <CardMedia
          className={classes.media}
          image="/img/my-picture.jpg"/>
)}
```





---

### Styled components
```
npm install styled-components
```

- React Components which have CSS styles embedded WITHIN the JS
- Styled components contain their own styles and are so easily reusable across the entire project
- No class names, easy to identify what styling goes with what

---

React and CSS

```javascript=
<h2 className="subtitle">Hello world</h2>
```

```css
h2.subtitle{
  font-size: 2em;
  color: blue;
}
```

---

Styled Components

```javascript=
import styled from 'styled-components';

const Subtitle = styled.h2`
  font-size: 2em;
  color: blue;
`;

<Subtitle>Hello world</Subtitle>
```

---

### Using both together

- Material UI's default rules will **override styled components** as they have higher specificity
- To override these, add class names or force specificity

```javascript=
 <AppBar classes={{root: 'my-root-class'}}
 
 styled(AppBar)`
      &.my-root-class {
        z-index: 1500;
      }
    `
    
    OR
        styled(AppBar)`
      && {
        z-index: 1500;
      }
    `
```


---

### Resources

[Styled Components](https://medium.com/styled-components/how-styled-components-works-618a69970421)

[More Styled Components](https://medium.com/styled-components/styled-components-getting-started-c9818acbcbbd)

[Material UI tutorial](https://reactgo.com/material-ui-react-tutorial/)

[Override Material UI](https://levelup.gitconnected.com/material-ui-styled-components-fff4d345fb07)
