# resource-workspace-rcl

The API documentation of the Workspace React component. Learn more about the props and CSS customization.

## Basic

```jsx
import { Card } from 'translation-helps-rcl';
import { makeStyles } from '@material-ui/core/styles';
import '../../css/resource-workspace-rcl.css';

const useStyles = makeStyles(() => ({
  root: {
    padding: 0,
    margin: '0 1px !important',
    height: '100%',
  },
  dragIndicator: {},
}));

const layout = {
  lg: [
    {"w":6,"h":1,"x":0,"y":0,"i":"1"},
    {"w":6,"h":1,"x":6,"y":2,"i":"2"},
    {"w":6,"h":1,"x":0,"y":2,"i":"3"},
    {"w":6,"h":1,"x":6,"y":0,"i":"4"},
    {"w":12,"h":1,"x":0,"y":1,"i":"5"},
  ]
};

function onLayoutChange(_layout, layouts) {
  console.log({ _layout, layouts })
  // in this method you could save current layouts in local storage and later restore on refresh
  console.log(`onLayoutChange: new resource layouts: ${JSON.stringify(layouts)}`);
}

const classes = useStyles();
const layoutWidths = [[1, 1], [1, 1], [1]];

<Workspace
  gridMargin={[15, 15]}
  classes={classes}
  layout={layout}
  onLayoutChange={onLayoutChange}
  layoutWidths={layoutWidths}
>
  <Card title="translationWords" classes={classes}>
    1
  </Card>
  <Card title="translationAcademy" classes={classes}>
    2
  </Card>
  <Card title="translationNotes" classes={classes}>
    3
  </Card>
  <Card title="translationQuestoins" classes={classes}>
    4
  </Card>
  <Card title="Open Bible Stories" classes={classes}>
    5
  </Card>
</Workspace>;
```

## Auto height

If `autoResize = {true}` then the height of the cards will be calculated relative to the height of the window. The rows parameter specifies how much to split the screen height. If you have, for example, an appbar or footer, and you want to take their height into account when calculating, then pass it in the "correctHeight" parameter.

```jsx
import { Card } from 'translation-helps-rcl';
import { makeStyles } from '@material-ui/core/styles';
import '../../css/resource-workspace-rcl.css';

const useStyles = makeStyles(() => ({
  root: {
    padding: 0,
    margin: '0 1px !important',
    height: '100%',
  },
  dragIndicator: {},
}));

const layout = {
  lg: [
    {"w":6,"h":3,"x":0,"y":0,"i":"1"},
    {"w":6,"h":3,"x":6,"y":2,"i":"2"},
    {"w":6,"h":3,"x":0,"y":2,"i":"3"},
    {"w":6,"h":3,"x":6,"y":0,"i":"4"},
    {"w":12,"h":3,"x":0,"y":1,"i":"5"},
  ]
};

const classes = useStyles();
const breakpoints = { lg: 800, md: 650, sm: 500, };

<Workspace
  gridMargin={[10, 20]}
  classes={classes}
  layout={layout}
  autoResize={true}
  rows={15}
  correctHeight={0}
  breakpoints={breakpoints}
>
  <Card title="translationWords" classes={classes}>
    1
  </Card>
  <Card title="translationAcademy" classes={classes}>
    2
  </Card>
  <Card title="translationNotes" classes={classes}>
    3
  </Card>
  <Card title="translationQuestoins" classes={classes}>
    4
  </Card>
  <Card title="Open Bible Stories" classes={classes}>
    5
  </Card>
</Workspace>;
```
