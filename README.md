# Card Grid Component

This Vue component displays a grid of cards with titles and subtitles, along with "Show more" and "View all" buttons to control the visibility of the cards.

## Features

- **Responsive Design**: The component adjusts the number of initially displayed cards based on the window width.
- **Show More/Less Functionality**: Allows users to expand or collapse the card grid.
- **Smooth Scrolling**: When collapsing the grid, the page smoothly scrolls back to the top of the card section.

## Component Overview

- **Responsive Card Grid**: The number of initially visible cards changes based on the window size:
  - For window widths less than or equal to 991px, 2 cards are shown.
  - For larger window widths, 6 cards are shown.

- **Expandable Grid**: Users can expand the grid to show all cards or collapse it to show only the initial set.

- **Smooth Scroll**: When collapsing the card grid, the view scrolls back to the top of the card section smoothly for a better user experience.

## Props and Reactive Variables

- **cards**: An array of card objects containing `id`, `title`, and `subtitle`.
- **initialCardCount**: A reactive variable to store the initial number of cards to display.
- **expanded**: A reactive boolean to track whether the card grid is expanded or not.
- **sectionRef**: A reference to the card section for smooth scrolling purposes.

## Computed Properties

- **visibleCards**: Computes the list of cards to be displayed based on the `expanded` state.
- **showMoreButton**: Determines whether to show the "Show more" button based on the number of cards.

## Methods

- **updateInitialCardCount**: Updates the initial card count based on the window size.
- **toggleExpand**: Toggles the expansion state of the card grid.
- **scrollToSection**: Smoothly scrolls to the top of the card section when collapsing the grid.

## Lifecycle Hooks

- **onMounted**: Sets the initial card count and adds a resize event listener.
- **onUnmounted**: Removes the resize event listener when the component is destroyed.

## Slots and Buttons

- **PrimaryButton**: Displays the "Show more" or "Show less" button based on the grid state.
- **SecondaryButton**: Displays the "View all" button (for future use or linking to a different page).

## Transitions

- **card-list**: A CSS transition for the card list, providing smooth enter and leave animations for the cards.

