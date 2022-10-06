<script>
    import Header from "./UI/Header.svelte";
    import MeetupGrid from "./Meetups/MeetupGrid.svelte";
    import TextInput from "./UI/TextInput.svelte";
    import Button from "./UI/Button.svelte";

    let title = '';
    let subtitle = '';
    let address = '';
    let description = '';
    let imageUrl = '';
    let email = '';

    let meetups = [
        {
            id: 'm1',
            title: 'Coding Bootcamp',
            subtitle: 'Learn to code in 2 hours',
            description: 'In this meetup, we will have some experts that teach you how to code',
            imageUrl: 'https://i.pinimg.com/736x/f2/ca/5d/f2ca5d622ff6ee67da7b308e59d55724.jpg',
            address: '27th Nerd Road, 32523 New York',
            contactEmail: 'code@test.com',
        },
        {
            id: 'm2',
            title: 'Swim Together',
            subtitle: 'Let\'s go for some swimming',
            description: 'We will simply swim some rounds!',
            imageUrl: 'https://www.yourswimlog.com/wp-content/uploads/2016/10/how-to-improve-your-swim-meet-warm-up-min.jpg',
            address: '27th Nerd Road, 32523 New York',
            contactEmail: 'swim@test.com',
        },
    ]

    function addMeetup() {
        const newMeetup = {
            id: Math.random().toString(),
            title: title,
            subtitle: subtitle,
            description: description,
            imageUrl: imageUrl,
            address: address,
            contactEmail: email,
        };
        // meetups.push(newMeetup); Does not work because it not trigger Svelte.
        meetups = [newMeetup, ...meetups];
    }
</script>

<style>
    main {
        margin-top: 5rem;
    }

    form {
        width: 30rem;
        max-width: 90%;
        margin: auto;
    }
</style>

<Header />

<main>
    <form on:submit|preventDefault="{addMeetup}">

        <TextInput 
        id="title" 
        label="Title" 
        value="{title}"
        on:input= {event => (title = event.target.value)}
        />
        <TextInput 
        id="subtitle" 
        label="Subtitle" 
        value="{subtitle}"
        on:input= {event => (subtitle = event.target.value)}
        />
        <TextInput 
        id="imageUrl" 
        label="Image Url" 
        value="{imageUrl}"
        on:input= {event => (imageUrl = event.target.value)}
        />
        <TextInput 
        id="address" 
        label="Address" 
        value="{address}"
        on:input= {event => (address = event.target.value)}
        />
        <TextInput 
        id="contactEmail" 
        label="Contact Email" 
        type="email" 
        value="{email}"
        on:input= {event => (email = event.target.value)}
        />
        <TextInput 
        id="description" 
        label="Description" 
        controlType="textarea"
        rows="3"
        value="{description}"
        on:input= {event => (description = event.target.value)}
        />
        <Button type="submit" caption="Save"/>
    </form>

    <MeetupGrid {meetups} />
</main>

