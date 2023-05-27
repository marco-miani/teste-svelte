<script>
    import Header from "./UI/Header.svelte";
    import MeetupGrid from "./Meetups/MeetupGrid.svelte";
    import TextInput from "./UI/TextInput.svelte";
    import Button from "./UI/Button.svelte";

    let title = "";
    let subtitle = "";
    let address = "";
    let email = "";
    let description = "";
    let imageUrl = "";

    let meetups = [
        {
            id: "m1",
            title: "Coding Bootcamp",
            subtitle: "Learn to code in 2hours",
            description:
                "In this meetup, we will have some experts that could teach you how to code.",
            imageUrl:
                "https://techcrunch.com/wp-content/uploads/2015/04/codecode.jpg",
            address: "123 Blabla Street",
            contactEmail: "marco@marco.com",
        },
        {
            id: "m2",
            title: "Swim Class",
            subtitle: "Let's go Swim!",
            description: "In this meetup, we will have some time swimming.",
            imageUrl:
                "https://learnenglishkids.britishcouncil.org/sites/kids/files/styles/max_325x325/public/RS2503_Swimming%20col-web.jpg?itok=rya0rO9j",
            address: "456 Blabla Street",
            contactEmail: "marco@marco.com",
        },
    ];

    function addMeetup() {
        const newMeetup = {
            id: Math.random().toString(),
            title: title,
            subtitle: subtitle,
            description: description,
            address: address,
            imageUrl: imageUrl,
            contactEmail: email,
        };

        meetups = [newMeetup, ...meetups];
    }
</script>

<Header />

<main>
    <form on:submit|preventDefault={addMeetup}>
        <TextInput
            id="title"
            label="Title"
            type="text"
            value={title}
            on:input={(event) => {
                title = event.target.value;
            }}
        />

        <TextInput
            id="subtitle"
            label="Subtitle"
            type="text"
            value={subtitle}
            on:input={(event) => {
                subtitle = event.target.value;
            }}
        />

        <TextInput
            id="imageUrl"
            label="ImageUrl"
            type="text"
            value={imageUrl}
            on:input={(event) => {
                imageUrl = event.target.value;
            }}
        />

        <TextInput
            id="email"
            label="E-mail"
            type="email"
            value={email}
            on:input={(event) => {
                email = event.target.value;
            }}
        />

        <TextInput
            id="address"
            label="Address"
            type="text"
            value={address}
            on:input={(event) => {
                address = event.target.value;
            }}
        />

        <TextInput
            id="description"
            label="Description"
            controlType="textarea"
            value={description}
            on:input={(event) => {
                description = event.target.value;
            }}
        />

        <Button type="submit" caption="Save"/>
    </form>
    <MeetupGrid {meetups} />
</main>

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
