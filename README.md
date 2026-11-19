# Agent Office

A 3D virtual office that shows a team of AI agents at work. When an agent picks up a task, its character stands up, walks to its station and performs an activity. When the task is done, it walks back, sits down and goes to standby.

The demo studio is **Brightframe Studio**, a content company run by six AI agents across four departments.

## Features

- **Isometric 3D office:** Executive, Production, Content and Finance rooms around a central hub, built with Three.js.
- **Agent states:** standby at the desk, walking, working at a station, and handing work to a teammate.
- **Station activities:** whiteboard, edit bay, recording mic, camera set, storyboard and filing cabinets, each reacting while its agent works.
- **Task pipeline:** plan → script → shoot → edit → dub → log costs, with handoffs between agents.
- **Live activity feed:** new tasks, progress, handoff messages and idle updates. Click the header to collapse it; a counter shows new events while it is closed.
- **Tasks, Brain and Inbox panels:** task status, shared studio notes, and approvals waiting for you.
- **Debug tools:** frame stats, agent commands (Coffee, Meeting, Visit, Back to desk), Wander mode and path lines. Press `D` to show or hide them.
- **Navigation:** drag to pan, scroll or pinch to zoom, and click a department to focus on its room.

## Run it

There is no build step. Open `index.html` in a modern browser, or serve the folder:

```bash
npx serve .
```

An internet connection is needed the first time, because Three.js and the Inter font load from public CDNs.

## Connect real agents

The page exposes a small API on `window.AgentOffice`. Turn off the built-in simulation, then call it from your agent runtime, for example over a WebSocket or from a polling script:

```js
AgentOffice.simulate(false);

// Agent stands up, walks to its station and works until completed
AgentOffice.startTask('jordan', 'Render the launch teaser');

// Agent walks back to its desk, sits down and returns to standby
AgentOffice.completeTask('jordan');

// Optional idle behaviour: 'coffee', 'meeting', 'visit' or 'desk'
AgentOffice.command('casey', 'coffee');
```

Agent IDs: `avery`, `jordan`, `casey`, `sam`, `riley`, `morgan`.

To use your own team, edit the `ROOMS` and `AGENTS` lists at the top of the script in `index.html`. Each agent has a name, role, room, colour, desk position, work station and activity.

## Tech stack

- [Three.js](https://threejs.org/) r128 for 3D rendering
- Plain HTML, CSS and JavaScript in one file, with no framework or build tools

## License

MIT, see [LICENSE](LICENSE).
