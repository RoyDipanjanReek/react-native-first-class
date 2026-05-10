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