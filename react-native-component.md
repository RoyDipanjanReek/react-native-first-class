import { useState } from "react";
import { Text, View,Image, TextInput, Pressable } from "react-native";

export default function HomeScreen(){
  const [name, setName] = useState("")
  return (
    <View>
      <Text numberOfLines={3}>
      hello world! Lorem ipsum dolor sit amet consectetur, adipisicing elit. Perferendis a enim unde nobis laudantium natus veritatis quo perspiciatis distinctio facilis. Placeat eveniet delectus cumque minus culpa. Blanditiis amet deleniti sapiente.
      </Text>

      <Image 
      source={{uri: "https://www.shutterstock.com/image-photo/sun-sets-behind-mountain-ranges-600nw-2479236003.jpg",}}
      blurRadius={40}
      width={200}
      height={200}
      />


      <TextInput 
      placeholder="Enter your name"
      value={name}
      onChangeText={setName}
      placeholderTextColor={"red"}
      style={{
        borderWidth: 1,
        borderColor: "#ddd",
        marginTop: 10, 
        fontSize: 24
      }}
      />

      <Pressable 
    
      onPress={() => alert("Button Pressed")}
        style={
          ({pressed}) => ({
            backgroundColor:pressed ? "red" : "blue"
          })
        }
        >
        <Text>Press me</Text>
      </Pressable>
    </View>
  )
}



import { Button, ScrollView, StyleSheet, Switch, Text, View } from 'react-native'
import React, { useState } from 'react'

const HomeScreen = () => {

  const items = Array.from({ length:2 }, (_, i) => `Item ${i + 1}`)

  const [isdarkMode, setIsDarkMode] = useState(false)
  return (
    <ScrollView
    contentContainerStyle={{
      padding:16,
      alignItems:"center"
    }}
    >
      {items.map((item) => (
        <View
        key={item}
        style={{
          backgroundColor: "white",
          padding: 16,
          borderRadius: 10,
          marginBottom: 10,
          shadowColor: "#000",
          shadowOpacity: 0.05,
          shadowRadius: 4,
          elevation: 2
        }}
        >

          <Button 
          title='Hello I am button' 
          color={"green"} 
          onPress={() => alert("Hello world")}
          />


          <Switch 
          value={isdarkMode} 
          onValueChange={setIsDarkMode} 
          trackColor={{false: "#ddd", true: "#6c63ff"}}
          thumbColor={"yellow"}
          />
        </View>
      ))}
    </ScrollView>
  )
}

export default HomeScreen

const styles = StyleSheet.create({})





import { StyleSheet, Text, View, FlatList } from 'react-native'
import React from 'react'


const USERS = [
  { id: '1', name: "abcd", role: "Designer"},
  { id: '2', name: "abcde", role: "Des"},
  { id: '3', name: "abcdef", role: "Designer freasher"},
  { id: '4', name: "abcdefgh", role: "Developer"},
]


const index = () => {
  return (
    <FlatList
    data={USERS}
    horizontal
    keyExtractor={(item) => item.id}
    contentContainerStyle={{padding: 16}}
    renderItem={({item}) => <Text>{item.name}</Text>}
    
    />
  )
}

export default index

const styles = StyleSheet.create({})



////////////////////////////////////////////////////
//// Safe & unsafe area vieew
import { StyleSheet, Text, View, } from 'react-native'
import React from 'react'
import { SafeAreaView } from 'react-native-safe-area-context'

function UnsafeScreen(){
  return(
    <View style={{flex: 1, backgroundColor: "#1c1c1c"}}>
      <Text style={{color: "#fff", fontSize: 18, padding: 16}}>
        Header bleeds under notch!
      </Text>
      <Text style={{color: "#aaa", padding: 16}}>
        This context might be hidden behind the status bar in dark mode.
      </Text>
    </View>
  )
}


function SafeScreen(){
  return(
    <SafeAreaView edges={["bottom", "top"]} style={{flex: 1, backgroundColor: "#1c1c1c"}}>
      <Text style={{color: "#fff", fontSize: 18, padding: 16}}>
        Header safely below notch!
      </Text>
      <Text style={{color: "#aaa", padding: 16}}>
        This context respict the safe area on all devices.
      </Text>
    </SafeAreaView>
  )
}


const index = () => {
  return (
    <>
    <SafeScreen />
    {/* <UnsafeScreen /> */}
    </>
  )
}

export default index

const styles = StyleSheet.create({})

/////////////////////////////////////////////////////


import { StyleSheet, Text, View, StatusBar } from 'react-native'
import React from 'react'
import { initialWindowMetrics, SafeAreaProvider, useSafeAreaInsets } from 'react-native-safe-area-context'

const HomeScreen = () => {

  const insets = useSafeAreaInsets()
  return (
    // <View
    // style={{
    //   flex: 1,
    //   paddingTop: insets.top,
    //   paddingBottom: insets.bottom
    // }}
    // >
    //   <Text>HomeScreen</Text>
    // </View>


    // <SafeAreaProvider initialMetrics={initialWindowMetrics}></SafeAreaProvider>

    <View
    style={{
      flex: 1,
      paddingTop: insets.top,
      paddingBottom: insets.bottom
    }}
    >
      <StatusBar barStyle={"dark-content"} />
      <Text>HomeScreen</Text>
    </View>
  )
}

export default HomeScreen

const styles = StyleSheet.create({})


/////////////////////////////////////////////////
StyleSheet.compose && StyleSheet Create

import { StyleSheet, Text, View } from "react-native";
import React from "react";
import { SafeAreaView } from "react-native-safe-area-context";
import { StatusBar } from 'expo-status-bar';

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: "center"
  },
  button: {
    paddingVertical: 12,
    paddingHorizontal: 32,
    borderRadius: 10,
    backgroundColor: '#ccc'
  },
  activeButton: {
    backgroundColor: "#6c63ff"
  },
  buttonText: {
    color: 'white',
    fontWeight: 'bold',
    fontSize: 16
  }
})

const Homescreen = () => {
  const isActive = true

  const buttonStyle = StyleSheet.compose(
    styles.button,
    isActive ? styles.activeButton : null
  )
  return (
    <View style={styles.container}>
      {/**@ts-ignore */}
      <View style={buttonStyle}>
        <Text style={styles.buttonText}>Composed style</Text>
      </View>
    </View>
  );
};

export default Homescreen;

const styles = StyleSheet.create({
  card: {
    backgroundColor: "white",
    borderRadius: 16,
    padding: 20,
    margin: 16,
    elevation: 4, //For Andriod shadow
    // For IOS
    shadowColor: "#000",
    shadowOpacity: 0.1,
    shadowRadius: 8,
  },
  title: {
    fontSize: 20,
    fontWeight: "bold",
    color: "#333",
  },
  subTitle: {
    fontSize: 14,
    color: "#888",
    marginTop: 4,
  },
});


// /////////////////////////////////////////////////////////
StyleShit flatten
import { StyleSheet, Text, View } from 'react-native'
import React from 'react'



const stylesA = StyleSheet.create({
  text: {
    color: "red",
    fontSize: 16
  }
})
const stylesB = StyleSheet.create({
  text: {
    fontSize: 24,
    fontWeight: 'bold'
  }
})

const flat = StyleSheet.flatten([stylesA.text, stylesB.text])

const HomeScreen = () => {
  return (
   
      <Text style={flat}>Flattened Style</Text>
   
  )
}

export default HomeScreen




////////////////////////////////////////////
Portrait & Landscape
import {
  Pressable,
  StyleSheet,
  Text,
  View,
  useWindowDimensions,
} from "react-native";
import React from "react";
import * as ScreenOrientation from "expo-screen-orientation";

const HomeScreen = () => {
  const { height, width } = useWindowDimensions();

  const isTablet = width >= 768;
  const isLandScape = width > height;

  const lockLandScape = async () => {
    await ScreenOrientation.lockAsync(
      ScreenOrientation.OrientationLock.LANDSCAPE,
    );
  };
  const lockPortrait = async () => {
    await ScreenOrientation.lockAsync(
      ScreenOrientation.OrientationLock.PORTRAIT,
    );
  };

  return (
    <View style={{ flex: 1, padding: 16 }}>
      <Text style={{ fontSize: width * 0.06 }}>Responsive Text</Text>

      <View style={{ flexDirection: isTablet ? "row" : "column" }}>
        <View
          style={{
            width: isTablet ? width / 2 : width - 32,
            padding: 20,
            backgroundColor: "#6c63ff",
            borderRadius: 12,
            marginBottom: isTablet ? 0 : 12,
          }}
        >
          <Text style={{ color: "white" }}>card 1</Text>
        </View>
        <View
          style={{
            width: isTablet ? width / 2 : width - 32,
            padding: 20,
            backgroundColor: "#ff6584",
            borderRadius: 12,
          }}
        >
          <Text style={{ color: "white" }}>Card 2</Text>
        </View>
      </View>

      <Text style={{ color: " #888", marginTop: 16 }}>
        Screen: {Math.round(width)} * {Math.round(height)}
        {isLandScape ? " {Landspace}" : "(Portrait)"}
      </Text>


      <Pressable
        onPress={lockPortrait}
        style={{
          flex: 1,
          backgroundColor: "#ff6584",
          padding: 12,
          borderRadius: 8,
          alignItems: "center"
        }}
      >
        <Text style={{ color: "white" }}> Force Portrait</Text>
      </Pressable>
      <Pressable
        onPress={lockLandScape}
        style={{
          flex: 1,
          backgroundColor: "green",
          padding: 12,
          borderRadius: 8,
          alignItems: "center"
        }}
      >
        <Text style={{ color: "white" }}> Force Landscape</Text>
      </Pressable>
    </View>
  );
};

export default HomeScreen;

const styles = StyleSheet.create({});
